# @advertol/core

[![Build Status][ci-img]][ci] [![BrowserStack Status][browserstack-img]][browserstack]

Core module for creating Advertol instance.

## Install

```sh
npm install @advertol/core --save
```

## Usage

```js
import advertol from '@advertol/core';
import CustomAdServerService from './service';
import CustomControl from './control';
import CustomContext from './context';

const instance = advertol({
	zones: [{
		id: 'becky',
		element: document.querySelector('.Zone--becky')
	}],
	service: new CustomAdServerService(),
	control: [
		new CustomControl()
	],
	context: [
		new CustomContext()
	]
});

instance.resolve();
```

## API

### advertol(options)

Returns: `Advertol`

Create Advertol instance.

#### zones

Type: `Object[]`

List of zones.

| Property | Type | Description |
| --- | --- | --- |
| `element` | `HTMLElement` | Zone DOM element. |
| `id` | `string` | Zone ID. |

#### service

Type: `Service`

Advertisement server [service][service].

#### control

Type: `Control[]`

List of [controls][control] for Advertol instance.

#### context

Type: `Context[]`

List of [contexts][context] for Advertol instance.

### instance.resolve()

Returns: `Promise`

Resolves current instance state. This should be run first time and every time you add new zone, control or context to resolve new instance state.

### instance.addControl(control)

Add new [control][control].

#### control

Type: 'Control'

### instance.addContext(context)

Add new [context][context].

#### context

Type: 'Context'

### instance.addZone({ element, id })

Add new zone.

| Property | Type | Description |
| --- | --- | --- |
| `element` | `HTMLElement` | Zone DOM element. |
| `id` | `string` | Zone ID. |

### instance.destroy()

Destroy instance.

## Browser support

Tested in IE9+ and all modern browsers, assuming `Promise` support is available.

## Test

For automated tests, run `npm run test:automated` (append `:watch` for watcher support).

## License

MIT © [Ivan Nikolić](http://ivannikolic.com)

[ci]: https://travis-ci.com/niksy/advertol-core
[ci-img]: https://travis-ci.com/niksy/advertol-core.svg?branch=master
[browserstack]: https://www.browserstack.com/
[browserstack-img]: https://www.browserstack.com/automate/badge.svg?badge_key=YWxaem45M0tCRHNpTkdZdHdlcGx4WDg4eVB1RUlqUy8wWk5kSFowQXJrcz0tLURaMU5NcUJMOERDQ1pnNkZwcTM3bGc9PQ==--761e47cbb39133df6ee49bbb87b2f53c6c5ef579
[service]: https://github.com/niksy/advertol/docs/service.md
[control]: https://github.com/niksy/advertol/docs/control.md
[context]: https://github.com/niksy/advertol/docs/context.md
