
# React-Native-keyscan-event
React Native Android module use for listen native keyboard event, listen scan barcode event and can dismiss keyboard.

### Installation

```bash
npm install react-native-keyscan-event --save
react-native link react-native-keyscan-event
```

## Example usage

Javascript code

```javascript
import KeyScanEvent from 'react-native-keyscan-event'
...
componentDidMount() {
    KeyScanEvent.onBarcodeScanner((result) => {
        // do something with result
    });
    KeyScanEvent.onKeyUpListener((result) => {
        // do something with result
    });
}
componentWillUnmount() {
    KeyScanEvent.removeBarcodeScanner();
    KeyScanEvent.removeKeyUpListener();
}
```
Add react-native package in MainApplication.java
```java
import com.zhai.rnkeyscan.KeyScanPackage;
...
//  ReactNativeHost
	@Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
		new KeyScanPackage(),
      );
    }
...

```
Implement onKeyDown and onKeyUp in MainActivity.java
```java
import com.zhai.rnkeyscan.KeyScanModule;
import android.view.KeyEvent;
...
	@Override
    public boolean onKeyDown(int keyCode, KeyEvent event) {
		KeyScanModule.getInstance().onKeyDownEvent(keyCode, event);
		super.onKeyDown(keyCode, event);
        return true;
	}
	@Override
	public boolean onKeyUp(int keyCode, KeyEvent event) {
		KeyScanModule.getInstance().onKeyUpEvent(keyCode, event);
		super.onKeyUp(keyCode, event);
        return true;
	}
...

```

