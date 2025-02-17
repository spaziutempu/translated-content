---
title: Firefox 82 for developers
slug: Mozilla/Firefox/Releases/82
tags:
  - '82'
  - Firefox
  - Mozilla
  - Release
translation_of: Mozilla/Firefox/Releases/82
---
{{FirefoxSidebar}}

このページでは、開発者に影響する Firefox 82 の変更点をまとめています。Firefox 82 は、2020 年 10 月 20 日にリリースされました。

> **Note:** Mozilla Hacks の [Coming through with Firefox 82](https://hacks.mozilla.org/2020/10/coming-through-with-firefox-82/) もご覧ください。

## ウェブ開発者向けの変更点一覧

### 開発者ツール

- [ネットワークモニター](/ja/docs/Tools/Network_Monitor) を使用して [server-sent events を調査できる](/ja/docs/Tools/Network_Monitor/Inspecting_server-sent_events) ようになりました ({{bug(1640857)}})。
- ネットワークモニターの*メッセージ*パネルを*応答*パネルに統合しました。メッセージ (例えば WebSockets や server-sent events) を応答の一覧で確認できます ({{bug(1636421)}})。

### HTML

- [`<input type="color">`](/ja/docs/Web/HTML/Element/input/color) で使用するカラーピッカーが、キーボードで操作可能になりました ({{bug(1526820)}})。
- [`<iframe sandbox>`](/ja/docs/Web/HTML/Element/iframe) 属性の `allow-downloads` フラグをサポートしました ({{bug(1656212)}})。

### CSS

- {{CSSxRef("::file-selector-button", "::file-selector-button")}} 疑似要素を新たにサポートしました。この疑似要素は、[`<input type="file">`](/ja/docs/Web/HTML/Element/input/file) 要素の内部にあるファイル選択ボタンを表します ({{bug(1635675)}}, {{bug(1662478)}})。
- {{CSSxRef(":is", ":is()")}} および {{CSSxRef(":where", ":where()")}} 疑似クラスのエラー回復を改良しました。これらの疑似クラスは寛容なセレクターリストを受け入れるようになり、リスト内に無効なセレクターがあってもリスト全体が無効にはなりません ({{bug(1664718)}})。
- `appearance: button` をボタンのみに適用するようになりました。従って、{{CSSxRef("appearance")}} の値 `button` は `auto` のように動作します ({{bug(1662703)}})。

#### 廃止

- 独自仕様である [`:-moz-user-disabled`](/ja/docs/Web/CSS/:-moz-user-disabled) 疑似クラスを削除しました ({{bug(1664432)}})。

### HTTP

- HTML [`<a>`](/ja/docs/Web/HTML/Element/a) 要素で `download` 属性が設定されている場合 ([同一オリジンの URL](/ja/docs/Web/Security/Same-origin_policy)) に、[`Content-Disposition`](/ja/docs/Web/HTTP/Headers/Content-Disposition) ヘッダーの `inline` ディレクティブが無視されるようになりました。`Content-Disposition` ヘッダーの `filename` を設定すると、`download` 属性で指定したファイル名より優先して使用されますので注意してください ({{bug(1658877)}})。

### API

#### 新規 API

- [Media Session API](/ja/docs/Web/API/Media_Session_API) をデフォルトで有効にしました ({{bug(1665496)}})。

#### DOM

- [`Document.execCommand()`](/ja/docs/Web/API/Document/execCommand) の入れ子または再帰的な呼び出しのサポートを廃止して、`false` が返るようになりました ({{bug(1634262)}})。
- [仕様書](https://w3c.github.io/pointerevents/#setting-pointer-capture) に従って、[`Element.setPointerCapture()`](/ja/docs/Web/API/Element/setPointerCapture) でポインターの `id` が無効である場合に `NotFoundError` 例外が発生するようになりました ({{bug(1662124)}})。以前は誤って `InvalidPointerId` 例外が発生していました。
- タブで別のドメインからページを読み込んだときに [`window.name`](/ja/docs/Web/API/Window/name) プロパティを空文字列リセットして、元のページが (例えば "戻る" ボタンで) 再読み込みされたときに復元するようになりました。これは信頼されないページが、前のページが変数に保存していた可能性がある情報にアクセスすることを防ぎます。この変更は、ドメイン間のメッセージ送信に `window.name` を使用するフレームワークに影響があります ({{bug(444222)}})。

### WebDriver conformance (Marionette)

- より現実的なユーザーナビゲーションをシミュレートするため、サポートされるすべてのナビゲーションコマンドを親プロセスに移動しました ({{bug(1612831)}})。
- WebDriver 仕様書との適合性を向上させるため、すべてのコマンドで現在またはトップレベルのブラウジングコンテキストの確認を更新しました ({{bug(1493108)}})。
- `WebDriver:ElementClick` で、click イベントが実際に合成される前にコマンドが返る場合がある不具合を修正しました ({{bug(1394354)}})。

## アドオン開発者向けの変更点

- [`tabs.captureTab()`](/ja/docs/Mozilla/Add-ons/WebExtensions/API/tabs/captureTab) および [`tabs.captureVisibleTab()`](/ja/docs/Mozilla/Add-ons/WebExtensions/API/tabs/captureVisibleTab) メソッドで、与えた [`options`](/ja/docs/Mozilla/Add-ons/WebExtensions/API/extensionTypes/ImageDetails) オブジェクトの `rect` プロパティで関連するタブのコンテンツ領域を取得する、あるいはオブジェクトを与えない場合にタブで見えている領域を取得することが可能になりました ({{bug(1636508)}})。以前は `rect` プロパティが使用できず、これらのメソッドは常に関連するタブで見ている領域を取得していました。

## 過去のバージョン

{{Firefox_for_developers(81)}}
