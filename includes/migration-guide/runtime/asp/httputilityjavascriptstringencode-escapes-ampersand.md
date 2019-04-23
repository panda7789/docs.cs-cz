---
ms.openlocfilehash: 0056baa1e5f0cdc5bfcf8b0e83c9490ec5722926
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981540"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="193d8-101">Řídicí sekvence ampersand HttpUtility.JavaScriptStringEncode</span><span class="sxs-lookup"><span data-stu-id="193d8-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

|   |   |
|---|---|
|<span data-ttu-id="193d8-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="193d8-102">Details</span></span>|<span data-ttu-id="193d8-103">Od verze rozhraní .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> řídicí sekvence ampersand (&amp;) znaků.</span><span class="sxs-lookup"><span data-stu-id="193d8-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> escapes the ampersand (&amp;) character.</span></span>|
|<span data-ttu-id="193d8-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="193d8-104">Suggestion</span></span>|<span data-ttu-id="193d8-105">Pokud vaše aplikace závisí na předchozím chování této metody, můžete přidat nastavení ASPNET: javascriptdonotencodeampersand [prvku ASP.NET appSettings](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="193d8-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>|
|<span data-ttu-id="193d8-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="193d8-106">Scope</span></span>|<span data-ttu-id="193d8-107">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="193d8-107">Minor</span></span>|
|<span data-ttu-id="193d8-108">Version</span><span class="sxs-lookup"><span data-stu-id="193d8-108">Version</span></span>|<span data-ttu-id="193d8-109">4.5</span><span class="sxs-lookup"><span data-stu-id="193d8-109">4.5</span></span>|
|<span data-ttu-id="193d8-110">Type</span><span class="sxs-lookup"><span data-stu-id="193d8-110">Type</span></span>|<span data-ttu-id="193d8-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="193d8-111">Runtime</span></span>|
|<span data-ttu-id="193d8-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="193d8-112">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
