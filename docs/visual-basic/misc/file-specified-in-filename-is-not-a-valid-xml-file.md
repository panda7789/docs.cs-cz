---
title: Soubor zadaný v názvu souboru není platný soubor XML
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: 89499b07e767bd0b3a777db4e5155f64a4357f0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052310"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="d065b-102">Soubor zadaný v názvu souboru není platný soubor XML</span><span class="sxs-lookup"><span data-stu-id="d065b-102">File specified in FileName is not a valid XML file</span></span>

<span data-ttu-id="d065b-103">Název souboru, který jste zadali, není platný soubor XML.</span><span class="sxs-lookup"><span data-stu-id="d065b-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="d065b-104">K určení povolených struktuře a obsahu dokumentu XML, můžete dokumentu typ definice (DTD), Microsoft XML-Data Reduced (XDR) schématu nebo jazyk (XSD) schématu definice schématu XML.</span><span class="sxs-lookup"><span data-stu-id="d065b-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="d065b-105">XSD schémata jsou preferovaným způsobem, jak určit gramatiky XML v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d065b-105">XSD schemas are the preferred way to specify XML grammars in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>

> [!NOTE]
> <span data-ttu-id="d065b-106">V některých dřívějších verzích sady Visual Studio **XML – návrhář** se návrhář pro typové datové sady a schématu XML.</span><span class="sxs-lookup"><span data-stu-id="d065b-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="d065b-107">**XML – návrhář** je stále možné vytvářet a upravovat soubory schémat XML.</span><span class="sxs-lookup"><span data-stu-id="d065b-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="d065b-108">V sadě Visual Studio 2012, návrháře pro vytváření a úpravu typové datové sady je ale **Návrhář Dataset**.</span><span class="sxs-lookup"><span data-stu-id="d065b-108">However, in Visual Studio 2012, the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="d065b-109">Další informace najdete v tématu [vytváření a úpravy typované datové sady](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="d065b-109">For more information, see [Creating and Editing Typed Datasets](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d065b-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d065b-110">To correct this error</span></span>

- <span data-ttu-id="d065b-111">Zkontrolujte, že zadáváte správný název souboru.</span><span class="sxs-lookup"><span data-stu-id="d065b-111">Check that you are supplying the correct file name.</span></span>

- <span data-ttu-id="d065b-112">Zkontrolujte, zda zadaný soubor obsahuje platný kód XML načtením souboru XML, který chcete zkontrolovat do **XML – návrhář**.</span><span class="sxs-lookup"><span data-stu-id="d065b-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="d065b-113">Z **XML** nabídky, klikněte na tlačítko **ověřit XML**.</span><span class="sxs-lookup"><span data-stu-id="d065b-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="d065b-114">Chyby zobrazují v **seznamu úkolů**.</span><span class="sxs-lookup"><span data-stu-id="d065b-114">Errors are displayed in the **Task List**.</span></span>

- <span data-ttu-id="d065b-115">Pokud má soubor XML přidružené schéma XML, zkontrolujte, že se elementy zobrazí ve struktuře definovaná a, obsah jednotlivých prvků odpovídá deklarovanému datovému typy určená ve schématu.</span><span class="sxs-lookup"><span data-stu-id="d065b-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>

## <a name="see-also"></a><span data-ttu-id="d065b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d065b-116">See also</span></span>

- <xref:System.Xml>
- [<span data-ttu-id="d065b-117">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="d065b-117">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)