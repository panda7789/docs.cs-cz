---
ms.openlocfilehash: 418bcdca1e9a325894891d7b0e080ce035e2d1b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614460"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a><span data-ttu-id="6ad54-101">Vylepšení přístupnosti ASP.NET v .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="6ad54-101">ASP.NET Accessibility Improvements in .NET Framework 4.7.1</span></span>

#### <a name="details"></a><span data-ttu-id="6ad54-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6ad54-102">Details</span></span>

<span data-ttu-id="6ad54-103">Počínaje .NET Framework 4.7.1, ASP.NET zlepšila, jak webové ovládací prvky ASP.NET pracují s technologiemi usnadnění v aplikaci Visual Studio, aby lépe podporovaly ASP.NET zákazníky.</span><span class="sxs-lookup"><span data-stu-id="6ad54-103">Starting with the .NET Framework 4.7.1, ASP.NET has improved how ASP.NET Web Controls work with accessibility technology in Visual Studio to better support ASP.NET customers.</span></span>  <span data-ttu-id="6ad54-104">Mezi ně patří tyto změny:</span><span class="sxs-lookup"><span data-stu-id="6ad54-104">These include the following changes:</span></span>

- <span data-ttu-id="6ad54-105">Změny pro implementaci chybějících vzorů přístupnosti uživatelského rozhraní v ovládacích prvcích, jako je dialogové okno Přidat pole v průvodci zobrazení podrobností nebo dialogové okno Konfigurovat ListView Průvodce ListView.</span><span class="sxs-lookup"><span data-stu-id="6ad54-105">Changes to implement missing UI accessibility patterns in controls, like the Add Field dialog in the Details View wizard, or the Configure ListView dialog of the ListView wizard.</span></span>
- <span data-ttu-id="6ad54-106">Změny pro zlepšení zobrazení v režimu Vysoký kontrast, jako je například editor polí datového pageru.</span><span class="sxs-lookup"><span data-stu-id="6ad54-106">Changes to improve the display in High Contrast mode, like the Data Pager Fields Editor.</span></span>
- <span data-ttu-id="6ad54-107">Změny pro zlepšení prostředí navigace klávesnicí pro ovládací prvky, jako je dialogové okno pole v průvodci úpravou polí stránkování ovládacího prvku DataPager, dialogové okno Konfigurovat ObjectContext nebo dialogové okno Konfigurovat výběr dat v Průvodci konfigurací zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="6ad54-107">Changes to improve the keyboard navigation experiences for controls, like the Fields dialog in the Edit Pager Fields wizard of the DataPager control, the Configure ObjectContext dialog, or the Configure Data Selection dialog of the Configure Data Source wizard.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6ad54-108">Návrh</span><span class="sxs-lookup"><span data-stu-id="6ad54-108">Suggestion</span></span>

<span data-ttu-id="6ad54-109">**Jak vyjádřit nebo odhlásit tyto změny** Aby mohl Návrhář sady Visual Studio těžit z těchto změn, musí běžet na .NET Framework 4.7.1 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="6ad54-109">**How to opt in or out of these changes** In order for the Visual Studio Designer to benefit from these changes, it must run on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="6ad54-110">Webová aplikace může tyto změny využít v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="6ad54-110">The web application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="6ad54-111">Nainstalujte Visual Studio 2017 15,3 nebo novější, které ve výchozím nastavení podporují nové funkce usnadnění s následujícím přepínačem AppContext.</span><span class="sxs-lookup"><span data-stu-id="6ad54-111">Install Visual Studio 2017 15.3 or later, which supports the new accessibility features with the following AppContext Switch by default.</span></span>
- <span data-ttu-id="6ad54-112">Odsouhlasení se starším chováním funkce usnadnění přidáním `Switch.UseLegacyAccessibilityFeatures` přepínače AppContext do `<runtime>` oddílu v souboru devenv.exe.config a jeho nastavením na `false` , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="6ad54-112">Opt out of the legacy accessibility behaviors by adding the `Switch.UseLegacyAccessibilityFeatures` AppContext switch to the `<runtime>` section in the devenv.exe.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
<runtime>
...
<!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
...
</runtime>
</configuration>
```

<span data-ttu-id="6ad54-113">Aplikace, které cílí na .NET Framework 4.7.1 nebo novější a chtějí zachovat starší funkce usnadnění, se můžou přihlásit k používání starších funkcí pro usnadnění přístupu tím, že explicitně nastaví tento přepínač AppContext na `true` .</span><span class="sxs-lookup"><span data-stu-id="6ad54-113">Applications that target the .NET Framework 4.7.1 or later and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="6ad54-114">Name</span><span class="sxs-lookup"><span data-stu-id="6ad54-114">Name</span></span>    | <span data-ttu-id="6ad54-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6ad54-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6ad54-116">Rozsah</span><span class="sxs-lookup"><span data-stu-id="6ad54-116">Scope</span></span>   | <span data-ttu-id="6ad54-117">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="6ad54-117">Minor</span></span>       |
| <span data-ttu-id="6ad54-118">Verze</span><span class="sxs-lookup"><span data-stu-id="6ad54-118">Version</span></span> | <span data-ttu-id="6ad54-119">4.7.1</span><span class="sxs-lookup"><span data-stu-id="6ad54-119">4.7.1</span></span>       |
| <span data-ttu-id="6ad54-120">Typ</span><span class="sxs-lookup"><span data-stu-id="6ad54-120">Type</span></span>    | <span data-ttu-id="6ad54-121">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="6ad54-121">Retargeting</span></span> |
