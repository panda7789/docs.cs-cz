---
title: Při kompilování schémat XML v projektu došlo k chybám.
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 17886ececbd418ae60d6321c7a6278a1e982b9af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611277"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="e971a-102">Při kompilování schémat XML v projektu došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="e971a-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="e971a-103">Při kompilování schémat XML v projektu došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="e971a-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="e971a-104">Z tohoto důvodu není k dispozici technologie IntelliSense jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="e971a-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="e971a-105">Dojde k chybě ve schématu definice schématu XML (XSD), který je zahrnutý v projektu.</span><span class="sxs-lookup"><span data-stu-id="e971a-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="e971a-106">K této chybě dochází, když přidáte souboru XSD schématu (XSD), který je v konfliktu s existující schéma XSD nastaven pro projekt.</span><span class="sxs-lookup"><span data-stu-id="e971a-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="e971a-107">**ID chyby:** BC36810</span><span class="sxs-lookup"><span data-stu-id="e971a-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e971a-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e971a-108">To correct this error</span></span>  
  
-   <span data-ttu-id="e971a-109">Poklikejte na ikonu upozornění v **seznamu chyb** okna.</span><span class="sxs-lookup"><span data-stu-id="e971a-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="e971a-110">Visual Basic přejdete do umístění v souboru XSD, které je zdrojem upozornění.</span><span class="sxs-lookup"><span data-stu-id="e971a-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="e971a-111">Oprava chyby ve schématu XSD.</span><span class="sxs-lookup"><span data-stu-id="e971a-111">Correct the error in the XSD schema.</span></span>  
  
-   <span data-ttu-id="e971a-112">Ujistěte se, že všechny požadované soubory XSD (XSD) schématu jsou součástí projektu.</span><span class="sxs-lookup"><span data-stu-id="e971a-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="e971a-113">Budete muset kliknout na **zobrazit všechny soubory** na **projektu** nabídku zobrazte vaše XSD souborů **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="e971a-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="e971a-114">Klikněte pravým tlačítkem na soubor XSD a potom klikněte na tlačítko **zahrnout do projektu** k zahrnutí souboru do projektu.</span><span class="sxs-lookup"><span data-stu-id="e971a-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
-   <span data-ttu-id="e971a-115">Pokud používáte Průvodce XML na schéma, této chybě může dojít, pokud jste schémata odvodit více než jednou ze stejného zdroje.</span><span class="sxs-lookup"><span data-stu-id="e971a-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="e971a-116">V takovém případě existující soubory schématu XSD můžete odebrat z projektu, přidejte nový kód jazyka XML na schéma šablony položky a potom poskytnout XML na schéma průvodce všechny příslušné zdroje XML pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="e971a-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
-   <span data-ttu-id="e971a-117">Pokud se najde žádná chyba ve schématu XSD, kompilátor XML nemusí mít dostatek informací, které poskytují Podrobná chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="e971a-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="e971a-118">Je možné získat podrobnější informace o chybě, pokud je zajistit, že obory názvů XML pro soubory XSD součástí vašeho projektu zápasu obory názvů XML pro schéma XML, nastavte v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e971a-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e971a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e971a-119">See also</span></span>
- [<span data-ttu-id="e971a-120">Okno Seznam chyb</span><span class="sxs-lookup"><span data-stu-id="e971a-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)
- [<span data-ttu-id="e971a-121">XML</span><span class="sxs-lookup"><span data-stu-id="e971a-121">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
