# react-snippets-marco

## Install

VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=MarcoJang.react-snippets-marco

## Supported languages (file extensions)

-   TypeScript (.ts)
-   TypeScript React (.tsx)

## Snippets

Below is a list of all available snippets and the triggers of each one. The **⇥** means the `TAB` key.

|       Trigger | Content                                    |
| ------------: | ------------------------------------------ |
|        `rfc→` | `Create a React Arrow Function Component.` |
|       `rec->` | `Create a React Emotion Component.`        |
|       `rhc->` | `Create a React Hooks Component.`          |
|     `story->` | `Create a Storybook for component.`        |
|   `zustand->` | `Create a Zustand Store.`                  |
| `testh->` | `Create a Testing code for React Hook.`    |
| `testfc->` | `Create a React Fetch Component Testing Code`    |
| `testsb->` | `Create a State Testing Block.`    |


## Example

### rfc
```tsx
interface Props {}

export const Example = ({}: Props) => {
    return (
        <div>Example</div>
    )
};
```

### rec
```tsx
import styled from '@emotion/styled';

interface Props {}

export const Example = ({}: Props) => {
  return <Container>Example</Container>;
};

const Container = styled.div``;
```

### rhc
```tsx
interface Props {}

export const use = ({}: Props) => {
    return {};
};
```

### story
```tsx
import { Meta, Story } from "@storybook/react";
import { ComponentProps } from "react";
import { Example } from "./Example";

type Props = ComponentProps<typeof Example>;

const Template: Story<Props> = args => <Example {...args} />;

export const Default = Template.bind({});

Default.args = {};

export default {
	title: "Example.stories.ts",
	component: Example,
} as Meta;
```

### zustand
```tsx
import create from 'zustand';

interface State {
  value: string;
}

const initialState: State = {
  value: '',
};

export const useStore = create<State>((set) => ({
  ...initialState,
}));
```

### testh
```tsx
import { renderHook } from '@testing-library/react'
import { Example.test } from './Example.test';

const Spy = jest.spyOn(, );

describe('Example',() => {
   it('test name', () => {
      const { rerender } = renderHook(() => Example.test());
      expect(Spy).to();
   })
})
```

### testfc
```tsx
import { fireEvent, render, screen } from "@testing-library/react";
import { rest } from "msw";
import { setupServer } from "msw/node";

import { Example } from "./Example";

const MOCK_RESPONSE = {};

const server = setupServer(
	rest.get("/", (req, res, ctx) => {
		return res(ctx.json({ ...MOCK_RESPONSE }));
	})
);

beforeAll(() => server.listen());
afterEach(() => server.resetHandlers());
afterAll(() => server.close());
beforeEach(() => {
	render(<Example />);
});

describe("Test Example Component", () => {
	it("should render default UI before firing event", async () => {
		const defaultText = screen.getByText();
		expect(defaultText).toBeInTheDocument();
	});

	it("should render expected UI when firing event and fetching successfully", async () => {
		const target = screen.getByText();
		fireEvent.click(target);

		const data = await screen.findByText();
		expect(data).toBeInTheDocument();
	});

	it("should render error UI when fetching error", async () => {
		server.use(
			rest.get("/", (req, res, ctx) => {
				return res(ctx.status(404));
			})
		);

		const error = await screen.findByText();
		expect(error).toBeInTheDocument();
	});
});
```

### testsb
```tsx
it(' must have been called with updated state when firing  event', () => {
const Spy = jest.spyOn(window, '').mockImplementation()

    fireEvent.(target) // or userEvent

expect(Spy).toHaveBeenCalledTimes(1)
expect(Spy).toHaveBeenCalledWith(updated)
})
```

## License

MIT
