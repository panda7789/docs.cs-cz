---
title: Při kompilování schémat XML v projektu došlo k chybám.
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 919c6873ba63addb776d756a58c44a3fe3f0ec3d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409622"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="d8d6b-102">Při kompilování schémat XML v projektu došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="d8d6b-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="d8d6b-103">Při kompilování schémat XML v projektu došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="d8d6b-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="d8d6b-104">Z tohoto důvodu není k dispozici XML IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="d8d6b-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="d8d6b-105">V rámci schématu definice schématu XML (XSD), který je součástí projektu, je chyba.</span><span class="sxs-lookup"><span data-stu-id="d8d6b-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="d8d6b-106">K této chybě dochází, když přidáte soubor schématu XSD (. XSD), který je v konfliktu s existující sadou schémat XSD pro projekt.</span><span class="sxs-lookup"><span data-stu-id="d8d6b-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="d8d6b-107">**ID chyby:** BC36810</span><span class="sxs-lookup"><span data-stu-id="d8d6b-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d8d6b-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d8d6b-108">To correct this error</span></span>  
  
- <span data-ttu-id="d8d6b-109">Dvakrát klikněte na upozornění v okně **Seznam chyb** .</span><span class="sxs-lookup"><span data-stu-id="d8d6b-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="d8d6b-110">Visual Basic přejdete do umístění v souboru XSD, který je zdrojem upozornění.</span><span class="sxs-lookup"><span data-stu-id="d8d6b-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="d8d6b-111">Opravte chybu ve schématu XSD.</span><span class="sxs-lookup"><span data-stu-id="d8d6b-111">Correct the error in the XSD schema.</span></span>  
  
- <span data-ttu-id="d8d6b-112">Ujistěte se, že v projektu jsou zahrnuté všechny požadované soubory XSD schématu (. XSD).</span><span class="sxs-lookup"><span data-stu-id="d8d6b-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="d8d6b-113">Možná budete muset kliknout na **Zobrazit všechny soubory** v nabídce **projekt** a zobrazit soubory. xsd v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="d8d6b-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="d8d6b-114">Klikněte pravým tlačítkem na soubor. xsd a potom kliknutím na možnost **zahrnout do projektu** zahrňte soubor do projektu.</span><span class="sxs-lookup"><span data-stu-id="d8d6b-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
- <span data-ttu-id="d8d6b-115">Pokud používáte Průvodce XML na schéma, k této chybě může dojít, pokud ze stejného zdroje odvozujete schémata více než jednou.</span><span class="sxs-lookup"><span data-stu-id="d8d6b-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="d8d6b-116">V takovém případě můžete odebrat existující soubory schématu XSD z projektu, přidat novou šablonu XML do šablony položky schématu a potom poskytnout Průvodce schématu XML pro všechny příslušné zdroje XML pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="d8d6b-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
- <span data-ttu-id="d8d6b-117">Pokud ve schématu XSD není identifikována žádná chyba, kompilátor XML nemusí mít dostatek informací, aby mohl poskytovat podrobnou chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="d8d6b-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="d8d6b-118">Je možné získat podrobnější informace o chybách, pokud zajistíte, že obory názvů XML pro soubory. xsd zahrnuté ve vašem projektu odpovídají oborům názvů XML identifikovaným pro sadu schémat XML v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d8d6b-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8d6b-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8d6b-119">See also</span></span>

- [<span data-ttu-id="d8d6b-120">Seznam chyb okno</span><span class="sxs-lookup"><span data-stu-id="d8d6b-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)
- [<span data-ttu-id="d8d6b-121">XML</span><span class="sxs-lookup"><span data-stu-id="d8d6b-121">XML</span></span>](../../programming-guide/language-features/xml/index.md)
