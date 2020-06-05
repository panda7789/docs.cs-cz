---
title: Soubor zadaný v souboru FileName není platný soubor XML.
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: a84042490935e3e7e5a6de2a802d9effd5b4d3d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358345"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="c30c2-102">Soubor zadaný v souboru FileName není platný soubor XML.</span><span class="sxs-lookup"><span data-stu-id="c30c2-102">File specified in FileName is not a valid XML file</span></span>

<span data-ttu-id="c30c2-103">Název souboru, který jste zadali, není platný soubor XML.</span><span class="sxs-lookup"><span data-stu-id="c30c2-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="c30c2-104">Chcete-li určit povolenou strukturu a obsah dokumentu XML, můžete použít definici typu dokumentu (DTD), schéma XDR (Microsoft XML-data redukovaný) nebo schéma XML Schema Definition Language (XSD).</span><span class="sxs-lookup"><span data-stu-id="c30c2-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="c30c2-105">Schémata XSD jsou preferovaným způsobem, jak určit gramatiky XML v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c30c2-105">XSD schemas are the preferred way to specify XML grammars in the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="c30c2-106">V některých starších verzích sady Visual Studio je **Návrhář XML** návrhářem pro typové datové sady a schéma XML.</span><span class="sxs-lookup"><span data-stu-id="c30c2-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="c30c2-107">**Návrhář XML** lze nadále použít k vytvoření a úpravě souborů schémat XML.</span><span class="sxs-lookup"><span data-stu-id="c30c2-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="c30c2-108">V sadě Visual Studio 2012 je však Návrhář pro vytváření a úpravu typových datových sad **Návrhář datových sad**.</span><span class="sxs-lookup"><span data-stu-id="c30c2-108">However, in Visual Studio 2012, the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="c30c2-109">Další informace najdete v tématu [vytváření a úpravy zadaných datových sad](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="c30c2-109">For more information, see [Creating and Editing Typed Datasets](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c30c2-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c30c2-110">To correct this error</span></span>

- <span data-ttu-id="c30c2-111">Ověřte, zda jste zadali správný název souboru.</span><span class="sxs-lookup"><span data-stu-id="c30c2-111">Check that you are supplying the correct file name.</span></span>

- <span data-ttu-id="c30c2-112">Ověřte, zda zadaný soubor obsahuje platný kód XML načtením souboru XML, který chcete vrátit do **Návrháře XML**.</span><span class="sxs-lookup"><span data-stu-id="c30c2-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="c30c2-113">V nabídce **XML** klikněte na **ověřit XML**.</span><span class="sxs-lookup"><span data-stu-id="c30c2-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="c30c2-114">V **seznam úkolů**se zobrazují chyby.</span><span class="sxs-lookup"><span data-stu-id="c30c2-114">Errors are displayed in the **Task List**.</span></span>

- <span data-ttu-id="c30c2-115">Pokud má soubor XML přidružené schéma XML, ověřte, zda se prvky zobrazí v definované struktuře a zda obsah jednotlivých prvků odpovídá deklarovaným datovým typům, které jsou zadány ve schématu.</span><span class="sxs-lookup"><span data-stu-id="c30c2-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>

## <a name="see-also"></a><span data-ttu-id="c30c2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c30c2-116">See also</span></span>

- <xref:System.Xml>
- [<span data-ttu-id="c30c2-117">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="c30c2-117">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
