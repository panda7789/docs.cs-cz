---
title: "Soubor zadaný v názvu souboru není platný soubor XML"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3275608a1871ac981eb5b3aa39f0be6ab4e758e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="a8089-102">Soubor zadaný v názvu souboru není platný soubor XML</span><span class="sxs-lookup"><span data-stu-id="a8089-102">File specified in FileName is not a valid XML file</span></span>
<span data-ttu-id="a8089-103">Název souboru, který jste zadali, není platný soubor XML.</span><span class="sxs-lookup"><span data-stu-id="a8089-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="a8089-104">Chcete-li určit povolené struktuře a obsahu dokumentu XML, můžete použít definice typu dokumentu (DTD), schéma Microsoft XML-Data Reduced (XDR) nebo schématu schématu XML definition language (XSD).</span><span class="sxs-lookup"><span data-stu-id="a8089-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="a8089-105">XSD schémata jsou upřednostňovaný způsob, jak určit gramatika XML v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8089-105">XSD schemas are the preferred way to specify XML grammars in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8089-106">V některé starší verze sady Visual Studio **XML návrhář** je návrháře pro typové datové sady a schématu XML.</span><span class="sxs-lookup"><span data-stu-id="a8089-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="a8089-107">**XML návrhář** stále umožňuje vytvářet a upravovat soubory schématu XML.</span><span class="sxs-lookup"><span data-stu-id="a8089-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="a8089-108">Ale v [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], je návrháře pro vytváření a úpravy typové datové sady **návrháře Dataset**.</span><span class="sxs-lookup"><span data-stu-id="a8089-108">However, in [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="a8089-109">Další informace najdete v tématu [vytváření a úpravy typovaných datových sad](/visualstudio/data-tools/creating-and-editing-typed-datasets).</span><span class="sxs-lookup"><span data-stu-id="a8089-109">For more information, see [Creating and Editing Typed Datasets](/visualstudio/data-tools/creating-and-editing-typed-datasets).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a8089-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a8089-110">To correct this error</span></span>  
  
-   <span data-ttu-id="a8089-111">Zkontrolujte, že jsou poskytuje správný název souboru.</span><span class="sxs-lookup"><span data-stu-id="a8089-111">Check that you are supplying the correct file name.</span></span>  
  
-   <span data-ttu-id="a8089-112">Zkontrolujte, zda zadaný soubor obsahuje platný kód XML načtením souboru XML, který chcete zkontrolovat do **XML návrhář**.</span><span class="sxs-lookup"><span data-stu-id="a8089-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="a8089-113">Z **XML** nabídky, klikněte na tlačítko **ověřit XML**.</span><span class="sxs-lookup"><span data-stu-id="a8089-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="a8089-114">Chyby zobrazují v **seznam úkolů**.</span><span class="sxs-lookup"><span data-stu-id="a8089-114">Errors are displayed in the **Task List**.</span></span>  
  
-   <span data-ttu-id="a8089-115">Pokud soubor XML má přidružené schéma XML, zkontrolujte, že se objeví elementy ve struktuře definované a že obsah jednotlivých prvků odpovídá deklarované datové typy, určená ve schématu.</span><span class="sxs-lookup"><span data-stu-id="a8089-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8089-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8089-116">See Also</span></span>  
 <xref:System.Xml>  
 [<span data-ttu-id="a8089-117">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="a8089-117">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
