---
title: Lokalizace
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
ms.openlocfilehash: 68e877088c5c3d17b368561b563b4cb17d004e75
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278022"
---
# <a name="localization"></a><span data-ttu-id="3ebc1-102">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="3ebc1-102">Localization</span></span>

<span data-ttu-id="3ebc1-103">Lokalizace je proces překladu prostředků aplikace na lokalizované verze pro každou jazykovou verzi, kterou bude aplikace podporovat.</span><span class="sxs-lookup"><span data-stu-id="3ebc1-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="3ebc1-104">Do kroku lokalizace byste měli přejít až po dokončení kroku [kontroly lokalizace](localizability-review.md) , abyste ověřili, že je globální aplikace připravená na lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="3ebc1-104">You should proceed to the localization step only after completing the [Localizability Review](localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>

<span data-ttu-id="3ebc1-105">Aplikace, která je připravena k lokalizaci, je rozdělena do dvou koncepčních bloků: blok, který obsahuje všechny prvky uživatelského rozhraní a blok, který obsahuje spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="3ebc1-105">An application that is ready for localization is separated into two conceptual blocks: a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="3ebc1-106">Blok uživatelského rozhraní obsahuje pouze lokalizovatelné prvky uživatelského rozhraní, jako jsou například řetězce, chybové zprávy, dialogová okna, nabídky, vložené objekty objektů a tak dále pro neutrální jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="3ebc1-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="3ebc1-107">Blok kódu obsahuje pouze kód aplikace, který bude používán všemi podporovanými kulturami.</span><span class="sxs-lookup"><span data-stu-id="3ebc1-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="3ebc1-108">Modul CLR (Common Language Runtime) podporuje model prostředků satelitního sestavení, který odděluje spustitelný kód aplikace od jeho prostředků.</span><span class="sxs-lookup"><span data-stu-id="3ebc1-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="3ebc1-109">Další informace o implementaci tohoto modelu naleznete v tématu [prostředky v rozhraní .NET](../../framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="3ebc1-109">For more information about implementing this model, see [Resources in .NET](../../framework/resources/index.md).</span></span>

<span data-ttu-id="3ebc1-110">Pro každou lokalizovanou verzi vaší aplikace přidejte nové satelitní sestavení, které obsahuje lokalizovaný blok uživatelského rozhraní přeložený do příslušného jazyka pro cílovou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="3ebc1-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="3ebc1-111">Blok kódu pro všechny jazykové verze by měl zůstat stejný.</span><span class="sxs-lookup"><span data-stu-id="3ebc1-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="3ebc1-112">Kombinace lokalizované verze bloku uživatelského rozhraní s blokem kódu vytváří lokalizovanou verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="3ebc1-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>

<span data-ttu-id="3ebc1-113">Sada Windows Software Development Kit (SDK) poskytuje editor prostředků model Windows Forms (Winres. exe), který umožňuje rychle lokalizovat model Windows Forms pro cílové jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="3ebc1-113">The Windows Software Development Kit (SDK) supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="3ebc1-114">Informace o použití tohoto nástroje naleznete v tématu [Winres. exe (model Windows Forms editor prostředků)](../../framework/tools/winres-exe-windows-forms-resource-editor.md).</span><span class="sxs-lookup"><span data-stu-id="3ebc1-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3ebc1-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ebc1-115">See also</span></span>

- [<span data-ttu-id="3ebc1-116">Globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="3ebc1-116">Globalization and Localization</span></span>](index.md)
- [<span data-ttu-id="3ebc1-117">Kontrola lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="3ebc1-117">Localizability Review</span></span>](localizability-review.md)
- [<span data-ttu-id="3ebc1-118">Globalizace</span><span class="sxs-lookup"><span data-stu-id="3ebc1-118">Globalization</span></span>](globalization.md)
- [<span data-ttu-id="3ebc1-119">Prostředky v aplikacích klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="3ebc1-119">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
