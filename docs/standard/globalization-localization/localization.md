---
title: Lokalizace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4aaf2da77a1fab55cbebd6bfa05a2b1c74e5cbbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="localization"></a><span data-ttu-id="31fdd-102">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="31fdd-102">Localization</span></span>
<span data-ttu-id="31fdd-103">Lokalizace je proces převodu aplikace prostředky do lokalizované verze pro každou jazykovou verzi, která bude podporovat aplikace.</span><span class="sxs-lookup"><span data-stu-id="31fdd-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="31fdd-104">Až po dokončení byste měli přistoupit k lokalizaci [lokalizovatelnosti](../../../docs/standard/globalization-localization/localizability-review.md) kroku ověřte, že globalizovaná aplikace je připravena k lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="31fdd-104">You should proceed to the localization step only after completing the [Localizability Review](../../../docs/standard/globalization-localization/localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>  
  
 <span data-ttu-id="31fdd-105">Aplikace, která je připravena k lokalizaci je rozdělené do dvou konceptuálních bloků, blok, který obsahuje všechny prvky uživatelského rozhraní a blok, který obsahuje spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="31fdd-105">An application that is ready for localization is separated into two conceptual blocks, a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="31fdd-106">Bloky uživatelského rozhraní obsahuje pouze možnosti lokalizace uživatelského rozhraní prvky, jako jsou například řetězce, chybové zprávy, dialogových oken, nabídek, vložený objekt prostředky, a tak dále pro neutrální jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="31fdd-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="31fdd-107">Blok kódu obsahuje pouze kódu aplikace má být používána všechny podporované jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="31fdd-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="31fdd-108">Modul common language runtime podporuje model prostředků satelitních sestavení, oddělující spustitelný kód aplikace ze svých prostředků.</span><span class="sxs-lookup"><span data-stu-id="31fdd-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="31fdd-109">Další informace o implementaci tohoto modelu najdete v tématu [prostředků v aplikacích plochy](../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="31fdd-109">For more information about implementing this model, see [Resources in Desktop Apps](../../../docs/framework/resources/index.md).</span></span>  
  
 <span data-ttu-id="31fdd-110">Pro každou lokalizované verzi vaší aplikace přidáte nové satelitní sestavení, který obsahuje lokalizované uživatelské rozhraní bloku přeložit na příslušném jazyku u cílové jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="31fdd-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="31fdd-111">Blok kódu pro všechny jazykové verze by měla zůstat stejné.</span><span class="sxs-lookup"><span data-stu-id="31fdd-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="31fdd-112">Kombinace lokalizované verze bloku uživatelského rozhraní s blok kódu vytvoří lokalizovanou verzi vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="31fdd-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>  
  
 <span data-ttu-id="31fdd-113">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Dodává nástroj Windows Forms prostředků Editor (Winres.exe), který umožňuje rychle lokalizovat Windows Forms do cílové jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="31fdd-113">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="31fdd-114">Informace o použití tohoto nástroje najdete v tématu [Winres.exe (Editor prostředků Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span><span class="sxs-lookup"><span data-stu-id="31fdd-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31fdd-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="31fdd-115">See Also</span></span>  
 [<span data-ttu-id="31fdd-116">Globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="31fdd-116">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
 [<span data-ttu-id="31fdd-117">Revize lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="31fdd-117">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
 [<span data-ttu-id="31fdd-118">Globalizace</span><span class="sxs-lookup"><span data-stu-id="31fdd-118">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 [<span data-ttu-id="31fdd-119">Prostředky v aplikacích klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="31fdd-119">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
