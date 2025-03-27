# Unity.ZString

UPM package for [ZString](https://github.com/Cysharp/ZString).

The "official" way to install via GIT requires to add an additional DLL, I like to add my dependencies in `package.json` and be done with it.

## Installation

Add the dependency to your `manifest.json`

```json
{
  "dependencies": {
    "com.cysharp.zstring": "https://github.com/starburst997/Unity.ZString.git"
  }
}
```

## Usage

See the official [README](https://github.com/Cysharp/ZString?tab=readme-ov-file#getting-started).

```csharp
// same as x + y + z
_ = ZString.Concat(x, y, z);

// also can use numeric format strings
_ = ZString.Format("x:{0}, y:{1:000}, z:{2:P}",x, y, z);

_ = ZString.Join(',', x, y, z);

// for Unity, direct write(avoid string allocation completely) to TextMeshPro
tmp.SetTextFormat("Position: {0}, {1}, {2}", x, y, z);

// create StringBuilder
using(var sb = ZString.CreateStringBuilder())
{
    sb.Append("foo");
    sb.AppendLine(42);
    sb.AppendFormat("{0} {1:.###}", "bar", 123.456789);

    // and build final string
    var str = sb.ToString();

    // for Unity, direct write to TextMeshPro
    tmp.SetText(sb);

    // write to destination buffer
    sb.TryCopyTo(dest, out var written);
}
```

## Credits

Obviously a fork of [Cysharp/ZString](https://github.com/Cysharp/ZString).