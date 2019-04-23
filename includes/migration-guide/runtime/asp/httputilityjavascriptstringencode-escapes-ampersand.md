---
ms.openlocfilehash: 0056baa1e5f0cdc5bfcf8b0e83c9490ec5722926
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981540"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>Řídicí sekvence ampersand HttpUtility.JavaScriptStringEncode

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> řídicí sekvence ampersand (&amp;) znaků.|
|Doporučení|Pokud vaše aplikace závisí na předchozím chování této metody, můžete přidat nastavení ASPNET: javascriptdonotencodeampersand [prvku ASP.NET appSettings](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) v konfiguračním souboru.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
