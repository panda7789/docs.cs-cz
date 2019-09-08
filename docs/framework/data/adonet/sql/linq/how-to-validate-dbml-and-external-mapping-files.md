---
title: 'Postupy: Ověření DBML a externí soubory mapování'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: b5901705ac7c0692025ff1f4a4b78f976d62176d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793049"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="ba11e-102">Postupy: Ověření DBML a externí soubory mapování</span><span class="sxs-lookup"><span data-stu-id="ba11e-102">How to: Validate DBML and External Mapping Files</span></span>

<span data-ttu-id="ba11e-103">Externí soubory mapování a soubory. dbml, které upravíte, musí být ověřeny podle příslušných definic schémat.</span><span class="sxs-lookup"><span data-stu-id="ba11e-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="ba11e-104">Toto téma poskytuje uživatelům aplikace Visual Studio postupy pro implementaci procesu ověřování.</span><span class="sxs-lookup"><span data-stu-id="ba11e-104">This topic provides Visual Studio users with the steps to implement the validation process.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="ba11e-105">Ověření souboru. dbml nebo XML</span><span class="sxs-lookup"><span data-stu-id="ba11e-105">To validate a .dbml or XML file</span></span>

1. <span data-ttu-id="ba11e-106">V nabídce **soubor** v aplikaci Visual Studio přejděte na **otevřít**a potom klikněte na **soubor**.</span><span class="sxs-lookup"><span data-stu-id="ba11e-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>

2. <span data-ttu-id="ba11e-107">V dialogovém okně **otevřít soubor** klikněte na soubor mapování. dbml nebo XML, který chcete ověřit.</span><span class="sxs-lookup"><span data-stu-id="ba11e-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>

    <span data-ttu-id="ba11e-108">Soubor se otevře v **editoru XML**.</span><span class="sxs-lookup"><span data-stu-id="ba11e-108">The file opens in the **XML Editor**.</span></span>

3. <span data-ttu-id="ba11e-109">Klikněte pravým tlačítkem na okno a pak klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="ba11e-109">Right-click the window, and then click **Properties**.</span></span>

4. <span data-ttu-id="ba11e-110">V okně **vlastnosti** klikněte na tři tečky pro vlastnost **schémata** .</span><span class="sxs-lookup"><span data-stu-id="ba11e-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>

    <span data-ttu-id="ba11e-111">Otevře se dialogové okno **schémata XML** .</span><span class="sxs-lookup"><span data-stu-id="ba11e-111">The **XML Schemas** dialog box opens.</span></span>

5. <span data-ttu-id="ba11e-112">Všimněte si vhodné definice schématu pro svůj účel.</span><span class="sxs-lookup"><span data-stu-id="ba11e-112">Note the appropriate schema definition for your purpose.</span></span>

    - <span data-ttu-id="ba11e-113">DbmlSchema. xsd je definice schématu pro ověření souboru. dbml.</span><span class="sxs-lookup"><span data-stu-id="ba11e-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="ba11e-114">Další informace naleznete v tématu [generování kódu v LINQ to SQL](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ba11e-114">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>

    - <span data-ttu-id="ba11e-115">LinqToSqlMapping. xsd je definice schématu pro ověření externího souboru mapování XML.</span><span class="sxs-lookup"><span data-stu-id="ba11e-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="ba11e-116">Další informace najdete v tématu [externí mapování](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="ba11e-116">For more information, see [External Mapping](external-mapping.md).</span></span>

6. <span data-ttu-id="ba11e-117">Ve sloupci **použít** na požadovaném řádku definice schématu kliknutím otevřete rozevírací seznam a pak klikněte na **použít toto schéma**.</span><span class="sxs-lookup"><span data-stu-id="ba11e-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>

    <span data-ttu-id="ba11e-118">Definiční soubor schématu je nyní přidružen k vašemu souboru DBML nebo mapování XML.</span><span class="sxs-lookup"><span data-stu-id="ba11e-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>

    <span data-ttu-id="ba11e-119">Ujistěte se, že nejsou vybrány žádné jiné definice schématu.</span><span class="sxs-lookup"><span data-stu-id="ba11e-119">Make sure no other schema definitions are selected.</span></span>

7. <span data-ttu-id="ba11e-120">V nabídce **zobrazení** klikněte na příkaz **Seznam chyb**.</span><span class="sxs-lookup"><span data-stu-id="ba11e-120">On the **View** menu, click **Error List**.</span></span>

    <span data-ttu-id="ba11e-121">Určete, zda byly vygenerovány chyby, upozornění nebo zprávy.</span><span class="sxs-lookup"><span data-stu-id="ba11e-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="ba11e-122">V takovém případě je soubor XML platný proti definici schématu.</span><span class="sxs-lookup"><span data-stu-id="ba11e-122">If not, the XML file is valid against the schema definition.</span></span>

## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="ba11e-123">Alternativní metoda pro zadání definice schématu</span><span class="sxs-lookup"><span data-stu-id="ba11e-123">Alternate Method for Supplying Schema Definition</span></span>

<span data-ttu-id="ba11e-124">Pokud z nějakého důvodu není příslušný soubor. xsd zobrazen v dialogovém okně **schémat XML** , můžete stáhnout soubor. xsd z tématu nápovědy.</span><span class="sxs-lookup"><span data-stu-id="ba11e-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="ba11e-125">Následující kroky vám pomůžou uložit stažený soubor ve formátu Unicode, který vyžaduje editor XML sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ba11e-125">The following steps help you save the downloaded file in the Unicode format required by the Visual Studio XML Editor.</span></span>

#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="ba11e-126">Zkopírování souboru definice schématu z tématu nápovědy</span><span class="sxs-lookup"><span data-stu-id="ba11e-126">To copy a schema definition file from a Help topic</span></span>

1. <span data-ttu-id="ba11e-127">Vyhledejte téma nápovědy obsahující definici schématu, jak je popsáno dříve v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="ba11e-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>

    - <span data-ttu-id="ba11e-128">Pro soubory. dbml si přečtěte téma [generování kódu v LINQ to SQL](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ba11e-128">For .dbml files, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>

    - <span data-ttu-id="ba11e-129">Pro externí soubory mapování viz [externí mapování](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="ba11e-129">For external mapping files, see [External Mapping](external-mapping.md).</span></span>

2. <span data-ttu-id="ba11e-130">Kliknutím na **Kopírovat kód** zkopírujte soubor kódu do schránky.</span><span class="sxs-lookup"><span data-stu-id="ba11e-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>

3. <span data-ttu-id="ba11e-131">Spusťte Poznámkový blok pro vytvoření nového souboru.</span><span class="sxs-lookup"><span data-stu-id="ba11e-131">Start Notepad to create a new file.</span></span>

4. <span data-ttu-id="ba11e-132">Vložte kód ze schránky do souboru poznámkového bloku.</span><span class="sxs-lookup"><span data-stu-id="ba11e-132">Paste the code from the clipboard into Notepad file.</span></span>

5. <span data-ttu-id="ba11e-133">V nabídce **soubor** poznámkového bloku klikněte na **Uložit jako**.</span><span class="sxs-lookup"><span data-stu-id="ba11e-133">On the Notepad **File** menu, click **Save As**.</span></span>

6. <span data-ttu-id="ba11e-134">V poli **kódování** vyberte **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="ba11e-134">In the **Encoding** box, select **Unicode**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ba11e-135">Tento výběr zaručuje, že značka`FFFE`pořadí bajtů v kódování Unicode-16 je do textového souboru předpona.</span><span class="sxs-lookup"><span data-stu-id="ba11e-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>

7. <span data-ttu-id="ba11e-136">V poli **název souboru** vytvořte název souboru s příponou. xsd.</span><span class="sxs-lookup"><span data-stu-id="ba11e-136">In the **File name** box, create a file name with an .xsd extension.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba11e-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba11e-137">See also</span></span>

- [<span data-ttu-id="ba11e-138">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="ba11e-138">Reference</span></span>](reference.md)
