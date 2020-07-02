---
ms.openlocfilehash: 97299ddb9bee89c792ddb3d2b9c37516180996f7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614568"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a><span data-ttu-id="8488e-101">Vlastnost ContextMenuStrip. SourceControl obsahuje platný ovládací prvek v případě vnořeného ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="8488e-101">ContextMenuStrip.SourceControl property contains a valid control in the case of nested ToolStripMenuItems</span></span>

#### <a name="details"></a><span data-ttu-id="8488e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8488e-102">Details</span></span>

<span data-ttu-id="8488e-103">V .NET Framework 4.7.1 a předchozích verzích <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> vlastnost nesprávně vrací hodnotu null, pokud uživatel otevře nabídku z vnořených <xref:System.Windows.Forms.ToolStripMenuItem> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="8488e-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property incorrectly returns null when the user opens the menu from nested <xref:System.Windows.Forms.ToolStripMenuItem> controls.</span></span> <span data-ttu-id="8488e-104">V .NET Framework 4.7.2 a novějším <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> je vlastnost vždy nastavena na skutečný ovládací prvek zdroje.</span><span class="sxs-lookup"><span data-stu-id="8488e-104">In the .NET Framework 4.7.2 and later, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> property is always set to the actual source control.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8488e-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="8488e-105">Suggestion</span></span>

<span data-ttu-id="8488e-106">**Jak vyjádřit nebo odhlásit tyto změny** Aby aplikace mohla tyto změny využívat, musí běžet na .NET Framework 4.7.2 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="8488e-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="8488e-107">Aplikace může tyto změny využít v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="8488e-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="8488e-108">Cílí na .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="8488e-108">It targets the .NET Framework 4.7.2.</span></span> <span data-ttu-id="8488e-109">Tato změna je ve výchozím nastavení povolená v aplikacích model Windows Forms, které cílí na .NET Framework 4.7.2 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="8488e-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="8488e-110">Cílí na .NET Framework 4.7.1 nebo dřívější verzi a výslovný ze staršího chování přístupnosti přidáním následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do `<runtime>` oddílu app.config souboru a jeho nastavením na `false` , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="8488e-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

<span data-ttu-id="8488e-111">Aplikace, které cílí na .NET Framework 4.7.2 nebo novější a chtějí zachovat starší verze správy, se mohou vyjádřit k použití starší hodnoty správy zdrojového kódu explicitně nastavením tohoto přepínače AppContext na `true` .</span><span class="sxs-lookup"><span data-stu-id="8488e-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to the use of the legacy source control value by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="8488e-112">Name</span><span class="sxs-lookup"><span data-stu-id="8488e-112">Name</span></span>    | <span data-ttu-id="8488e-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8488e-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8488e-114">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8488e-114">Scope</span></span>   | <span data-ttu-id="8488e-115">Edge</span><span class="sxs-lookup"><span data-stu-id="8488e-115">Edge</span></span>        |
| <span data-ttu-id="8488e-116">Verze</span><span class="sxs-lookup"><span data-stu-id="8488e-116">Version</span></span> | <span data-ttu-id="8488e-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="8488e-117">4.7.2</span></span>       |
| <span data-ttu-id="8488e-118">Typ</span><span class="sxs-lookup"><span data-stu-id="8488e-118">Type</span></span>    | <span data-ttu-id="8488e-119">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="8488e-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8488e-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8488e-120">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>
