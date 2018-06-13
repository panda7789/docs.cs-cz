---
title: Při kompilování schémat XML v projektu došlo k chybám.
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 0cc565809792c619ca9903f9ef9b029b51a8aa17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588259"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="cde2e-102">Při kompilování schémat XML v projektu došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="cde2e-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="cde2e-103">Při kompilování schémat XML v projektu došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="cde2e-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="cde2e-104">Z toho důvodu XML IntelliSense není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="cde2e-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="cde2e-105">V definici schématu XML (XSD) schémat, která je zahrnutý v projektu dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="cde2e-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="cde2e-106">K této chybě dojde, když přidáte soubor XSD schématu (XSD), který je v konfliktu s existující schématu XSD nastavit pro projekt.</span><span class="sxs-lookup"><span data-stu-id="cde2e-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="cde2e-107">**ID chyby:** BC36810</span><span class="sxs-lookup"><span data-stu-id="cde2e-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cde2e-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="cde2e-108">To correct this error</span></span>  
  
-   <span data-ttu-id="cde2e-109">Klikněte dvakrát na upozornění v **seznamu chyb** okno.</span><span class="sxs-lookup"><span data-stu-id="cde2e-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="cde2e-110">Visual Basic přejdete do umístění v souboru XSD, který je zdrojem upozornění.</span><span class="sxs-lookup"><span data-stu-id="cde2e-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="cde2e-111">Opravte chybu ve schématu XSD.</span><span class="sxs-lookup"><span data-stu-id="cde2e-111">Correct the error in the XSD schema.</span></span>  
  
-   <span data-ttu-id="cde2e-112">Zkontrolujte, že všechny požadované soubory XSD schématu (.xsd) jsou zahrnuty v projektu.</span><span class="sxs-lookup"><span data-stu-id="cde2e-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="cde2e-113">Je třeba kliknout na **zobrazit všechny soubory** na **projektu** nabídky zobrazíte vaší XSD soubory v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="cde2e-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="cde2e-114">Klikněte pravým tlačítkem na soubor XSD a pak klikněte na **zahrnout do projektu** zahrnout soubor ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="cde2e-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
-   <span data-ttu-id="cde2e-115">Pokud používáte Průvodce XML na schéma, této chybě může dojít, pokud jste schémata odvození více než jednou z jednoho zdroje.</span><span class="sxs-lookup"><span data-stu-id="cde2e-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="cde2e-116">V takovém případě můžete odebrat existující soubory schématu XSD z projektu, přidat nové XML na schéma šablony položky a pak zadejte soubor XML na schéma průvodce s všechny příslušné zdroje XML pro projekt.</span><span class="sxs-lookup"><span data-stu-id="cde2e-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
-   <span data-ttu-id="cde2e-117">Pokud žádná chyba, je definovaný v schéma XSD, kompilátoru XML nemusí mít dostatek informací k poskytování Podrobná chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="cde2e-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="cde2e-118">Bude pravděpodobně možné získat podrobnější informace o chybě, pokud zajistíte, že obory názvů XML pro soubory XSD součástí vašeho projektu shodu obory názvů XML pro schéma XML nastavení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cde2e-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde2e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="cde2e-119">See Also</span></span>  
 [<span data-ttu-id="cde2e-120">Okno Seznam chyb</span><span class="sxs-lookup"><span data-stu-id="cde2e-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)  
 [<span data-ttu-id="cde2e-121">XML</span><span class="sxs-lookup"><span data-stu-id="cde2e-121">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
