---
title: 'Postupy: Ověření DBML a externí soubory mapování'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: b01bcf98bba185b7a4b1802f470a585371980177
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078730"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="36b26-102">Postupy: Ověření DBML a externí soubory mapování</span><span class="sxs-lookup"><span data-stu-id="36b26-102">How to: Validate DBML and External Mapping Files</span></span>
<span data-ttu-id="36b26-103">Externí soubory mapování a dbml soubory, které můžete upravit musí být ověřena jejich odpovídajících schématu definice.</span><span class="sxs-lookup"><span data-stu-id="36b26-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="36b26-104">Toto téma poskytuje uživatelům aplikace Visual Studio s kroky k implementaci procesu ověřování.</span><span class="sxs-lookup"><span data-stu-id="36b26-104">This topic provides Visual Studio users with the steps to implement the validation process.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="36b26-105">K ověření dbml nebo soubor XML</span><span class="sxs-lookup"><span data-stu-id="36b26-105">To validate a .dbml or XML file</span></span>  
  
1.  <span data-ttu-id="36b26-106">V sadě Visual Studio **souboru** nabídky, přejděte k **otevřít**a potom klikněte na tlačítko **souboru**.</span><span class="sxs-lookup"><span data-stu-id="36b26-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="36b26-107">V **otevřít soubor** dialogového okna klikněte na dbml nebo soubor mapování XML, který chcete ověřit.</span><span class="sxs-lookup"><span data-stu-id="36b26-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>  
  
     <span data-ttu-id="36b26-108">Soubor se otevře v **editoru XML**.</span><span class="sxs-lookup"><span data-stu-id="36b26-108">The file opens in the **XML Editor**.</span></span>  
  
3.  <span data-ttu-id="36b26-109">Klikněte pravým tlačítkem myši okno a potom klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="36b26-109">Right-click the window, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="36b26-110">V **vlastnosti** okna, klikněte na tlačítko se třemi tečkami pro **schémata** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="36b26-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>  
  
     <span data-ttu-id="36b26-111">**Schémat XML** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="36b26-111">The **XML Schemas** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="36b26-112">Mějte na paměti příslušného schématu definice pro požadovaný účel.</span><span class="sxs-lookup"><span data-stu-id="36b26-112">Note the appropriate schema definition for your purpose.</span></span>  
  
    -   <span data-ttu-id="36b26-113">DbmlSchema.xsd je definice schématu pro ověření souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="36b26-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="36b26-114">Další informace najdete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="36b26-114">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="36b26-115">LinqToSqlMapping.xsd je definice schématu pro ověřování externí soubor mapování XML.</span><span class="sxs-lookup"><span data-stu-id="36b26-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="36b26-116">Další informace najdete v tématu [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="36b26-116">For more information, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
6.  <span data-ttu-id="36b26-117">V **použití** sloupec řádku definice požadované schéma, otevřete rozevírací seznam a potom klepněte na tlačítko **použít tohle schéma**.</span><span class="sxs-lookup"><span data-stu-id="36b26-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>  
  
     <span data-ttu-id="36b26-118">Definiční soubor schématu je teď přidružené k vaší DBML nebo XML souboru mapování.</span><span class="sxs-lookup"><span data-stu-id="36b26-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>  
  
     <span data-ttu-id="36b26-119">Zkontrolujte, zda že jsou vybrány žádné definice schémat.</span><span class="sxs-lookup"><span data-stu-id="36b26-119">Make sure no other schema definitions are selected.</span></span>  
  
7.  <span data-ttu-id="36b26-120">Na **zobrazení** nabídky, klikněte na tlačítko **seznam chyb**.</span><span class="sxs-lookup"><span data-stu-id="36b26-120">On the **View** menu, click **Error List**.</span></span>  
  
     <span data-ttu-id="36b26-121">Určení, zda byly vytvořeny chyby, varování nebo zprávy.</span><span class="sxs-lookup"><span data-stu-id="36b26-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="36b26-122">V opačném případě je soubor XML platný pro definici schématu.</span><span class="sxs-lookup"><span data-stu-id="36b26-122">If not, the XML file is valid against the schema definition.</span></span>  
  
## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="36b26-123">Alternativní metoda pro poskytnutí definice schématu</span><span class="sxs-lookup"><span data-stu-id="36b26-123">Alternate Method for Supplying Schema Definition</span></span>  
 <span data-ttu-id="36b26-124">Pokud z nějakého důvodu odpovídající XSD souborů se nezobrazují v **schémat XML** dialogovém okně soubor XSD si můžete stáhnout z tématu nápovědy.</span><span class="sxs-lookup"><span data-stu-id="36b26-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="36b26-125">Následující kroky vám pomůžou ušetřit stažený soubor ve formátu Unicode, vyžaduje pomocí editoru XML sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36b26-125">The following steps help you save the downloaded file in the Unicode format required by the Visual Studio XML Editor.</span></span>  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="36b26-126">Zkopírujte soubor definice schématu z tématu nápovědy</span><span class="sxs-lookup"><span data-stu-id="36b26-126">To copy a schema definition file from a Help topic</span></span>  
  
1.  <span data-ttu-id="36b26-127">Téma nápovědy, který obsahuje definici schématu, jak je popsáno výše v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="36b26-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="36b26-128">Soubory dbml, naleznete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="36b26-128">For .dbml files, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="36b26-129">Externí soubory mapování, naleznete v tématu [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="36b26-129">For external mapping files, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
2.  <span data-ttu-id="36b26-130">Klikněte na tlačítko **kopírování kódu** do souboru s kódem zkopírujte do schránky.</span><span class="sxs-lookup"><span data-stu-id="36b26-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="36b26-131">Spusťte Poznámkový blok a vytvořte nový soubor.</span><span class="sxs-lookup"><span data-stu-id="36b26-131">Start Notepad to create a new file.</span></span>  
  
4.  <span data-ttu-id="36b26-132">Vložte kód ze schránky do soubor poznámkového bloku.</span><span class="sxs-lookup"><span data-stu-id="36b26-132">Paste the code from the clipboard into Notepad file.</span></span>  
  
5.  <span data-ttu-id="36b26-133">Na poznámkového bloku **souboru** nabídky, klikněte na tlačítko **uložit jako**.</span><span class="sxs-lookup"><span data-stu-id="36b26-133">On the Notepad **File** menu, click **Save As**.</span></span>  
  
6.  <span data-ttu-id="36b26-134">V **kódování** vyberte **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="36b26-134">In the **Encoding** box, select **Unicode**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="36b26-135">Tento výběr zaručuje, že značky pořadí bajtů kódování Unicode-16 (`FFFE`) se přidá jako předpona do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="36b26-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>  
  
7.  <span data-ttu-id="36b26-136">V **název_souboru** pole, vytvořte soubor s příponou XSD.</span><span class="sxs-lookup"><span data-stu-id="36b26-136">In the **File name** box, create a file name with an .xsd extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36b26-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36b26-137">See also</span></span>

- [<span data-ttu-id="36b26-138">Odkaz</span><span class="sxs-lookup"><span data-stu-id="36b26-138">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
