---
title: 'Postupy: ověření DBML a externí mapování souborů'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 9bf21353aebd0ae57c51b2ddf3b31b5e7f1ac615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362159"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="e4766-102">Postupy: ověření DBML a externí mapování souborů</span><span class="sxs-lookup"><span data-stu-id="e4766-102">How to: Validate DBML and External Mapping Files</span></span>
<span data-ttu-id="e4766-103">Externí mapování soubory a soubory dbml, které můžete upravit, musí být ověřený proti jejich definice příslušného schématu.</span><span class="sxs-lookup"><span data-stu-id="e4766-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="e4766-104">Toto téma poskytuje uživatelům sady Visual Studio s kroky k implementaci procesu ověření.</span><span class="sxs-lookup"><span data-stu-id="e4766-104">This topic provides Visual Studio users with the steps to implement the validation process.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="e4766-105">K ověření souboru XML nebo dbml</span><span class="sxs-lookup"><span data-stu-id="e4766-105">To validate a .dbml or XML file</span></span>  
  
1.  <span data-ttu-id="e4766-106">V sadě Visual Studio **soubor** nabídky, přejděte na příkaz **otevřete**a potom klikněte na **soubor**.</span><span class="sxs-lookup"><span data-stu-id="e4766-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="e4766-107">V **otevření souboru** dialogové okno pole, klikněte na dbml nebo mapování souboru XML, který chcete ověřit.</span><span class="sxs-lookup"><span data-stu-id="e4766-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>  
  
     <span data-ttu-id="e4766-108">Soubor se otevře v **editoru XML**.</span><span class="sxs-lookup"><span data-stu-id="e4766-108">The file opens in the **XML Editor**.</span></span>  
  
3.  <span data-ttu-id="e4766-109">Klikněte pravým tlačítkem na okna a pak klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="e4766-109">Right-click the window, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="e4766-110">V **vlastnosti** okně klikněte na tlačítko se třemi tečkami pro **schémata** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e4766-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>  
  
     <span data-ttu-id="e4766-111">**Schémat XML** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e4766-111">The **XML Schemas** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="e4766-112">Všimněte si definici příslušného schématu pro požadovaný účel.</span><span class="sxs-lookup"><span data-stu-id="e4766-112">Note the appropriate schema definition for your purpose.</span></span>  
  
    -   <span data-ttu-id="e4766-113">DbmlSchema.xsd je definice schématu pro ověření souboru DBML.</span><span class="sxs-lookup"><span data-stu-id="e4766-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="e4766-114">Další informace najdete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e4766-114">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="e4766-115">LinqToSqlMapping.xsd je definice schématu pro ověření externí mapování souboru XML.</span><span class="sxs-lookup"><span data-stu-id="e4766-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="e4766-116">Další informace najdete v tématu [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="e4766-116">For more information, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
6.  <span data-ttu-id="e4766-117">V **použití** sloupec požadované schéma definice řádku, klikněte na tlačítko Otevřít rozevíracího seznamu a pak klikněte na tlačítko **toto schéma používají**.</span><span class="sxs-lookup"><span data-stu-id="e4766-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>  
  
     <span data-ttu-id="e4766-118">Soubor definice schématu je teď přidružené k vaší DBML nebo mapování souboru XML.</span><span class="sxs-lookup"><span data-stu-id="e4766-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>  
  
     <span data-ttu-id="e4766-119">Zkontrolujte, zda že jsou vybrány žádné definice schémat.</span><span class="sxs-lookup"><span data-stu-id="e4766-119">Make sure no other schema definitions are selected.</span></span>  
  
7.  <span data-ttu-id="e4766-120">Na **zobrazení** nabídky, klikněte na tlačítko **seznam chyb**.</span><span class="sxs-lookup"><span data-stu-id="e4766-120">On the **View** menu, click **Error List**.</span></span>  
  
     <span data-ttu-id="e4766-121">Určí, zda byly vygenerovány chyby, upozornění nebo zprávy.</span><span class="sxs-lookup"><span data-stu-id="e4766-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="e4766-122">Pokud ne, je soubor XML platný proti definici schématu.</span><span class="sxs-lookup"><span data-stu-id="e4766-122">If not, the XML file is valid against the schema definition.</span></span>  
  
## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="e4766-123">Alternativní metoda pro zadávání definice schématu</span><span class="sxs-lookup"><span data-stu-id="e4766-123">Alternate Method for Supplying Schema Definition</span></span>  
 <span data-ttu-id="e4766-124">Pokud z nějakého důvodu odpovídající XSD souboru není uveden v **schémat XML** dialogové okno, soubor XSD můžete stáhnout z tématu nápovědy.</span><span class="sxs-lookup"><span data-stu-id="e4766-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="e4766-125">Následující kroky umožňují Uložte stažený soubor ve formátu Unicode požadované pomocí editoru XML sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e4766-125">The following steps help you save the downloaded file in the Unicode format required by the Visual Studio XML Editor.</span></span>  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="e4766-126">Zkopírujte soubor definice schématu z tématu nápovědy</span><span class="sxs-lookup"><span data-stu-id="e4766-126">To copy a schema definition file from a Help topic</span></span>  
  
1.  <span data-ttu-id="e4766-127">Najděte téma nápovědy, který obsahuje definici schématu, jak je popsáno výše v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="e4766-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="e4766-128">Soubory dbml, najdete v části [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e4766-128">For .dbml files, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="e4766-129">Externí mapování soubory, najdete v části [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="e4766-129">For external mapping files, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
2.  <span data-ttu-id="e4766-130">Klikněte na tlačítko **kopie kódu** při kopírování souboru kódu do schránky.</span><span class="sxs-lookup"><span data-stu-id="e4766-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="e4766-131">Spusťte program Poznámkový blok k vytvoření nového souboru.</span><span class="sxs-lookup"><span data-stu-id="e4766-131">Start Notepad to create a new file.</span></span>  
  
4.  <span data-ttu-id="e4766-132">Vložte kód ze schránky do souboru poznámkového bloku.</span><span class="sxs-lookup"><span data-stu-id="e4766-132">Paste the code from the clipboard into Notepad file.</span></span>  
  
5.  <span data-ttu-id="e4766-133">Na Poznámkový blok **soubor** nabídky, klikněte na tlačítko **uložit jako**.</span><span class="sxs-lookup"><span data-stu-id="e4766-133">On the Notepad **File** menu, click **Save As**.</span></span>  
  
6.  <span data-ttu-id="e4766-134">V **kódování** vyberte **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="e4766-134">In the **Encoding** box, select **Unicode**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e4766-135">Tento výběr zaručuje, že značky pořadí bajtů kódování Unicode-16 (`FFFE`) se přidá jako předpona do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="e4766-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>  
  
7.  <span data-ttu-id="e4766-136">V **název souboru** pole, vytvořte název souboru s příponou XSD.</span><span class="sxs-lookup"><span data-stu-id="e4766-136">In the **File name** box, create a file name with an .xsd extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4766-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4766-137">See Also</span></span>  
 [<span data-ttu-id="e4766-138">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="e4766-138">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
