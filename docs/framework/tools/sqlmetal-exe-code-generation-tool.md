---
title: "SqlMetal.exe (nástroj pro vytváření kódu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c14c01c670eccbc7f13210d3c0bb7df7bec07679
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="5a16c-102">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="5a16c-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="5a16c-103">Nástroj příkazového řádku na SqlMetal generuje kód a mapování [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] komponentu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a16c-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="5a16c-104">Použitím možností uvedených dále v tomto tématu můžete dát nástroji SqlMetal pokyn, aby provedl několik různých úkonů, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="5a16c-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
-   <span data-ttu-id="5a16c-105">Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování z databáze.</span><span class="sxs-lookup"><span data-stu-id="5a16c-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
-   <span data-ttu-id="5a16c-106">Vygenerování přechodného souboru .dbml (database markup language) z databáze za účelem přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="5a16c-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
-   <span data-ttu-id="5a16c-107">Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování ze souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="5a16c-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="5a16c-108">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a16c-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="5a16c-109">Ve výchozím nastavení, je uložen v souboru `drive`: \Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span><span class="sxs-lookup"><span data-stu-id="5a16c-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="5a16c-110">Pokud nenainstalujete Visual Studio, můžete získat také na SQLMetal soubor stáhněte [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225).</span><span class="sxs-lookup"><span data-stu-id="5a16c-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a16c-111">Vývojáři, kteří používají Visual Studio můžete také použít [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] ke generování tříd entit.</span><span class="sxs-lookup"><span data-stu-id="5a16c-111">Developers who use Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] to generate entity classes.</span></span> <span data-ttu-id="5a16c-112">Metoda využívající příkazový řádek je vhodná u velkých databází.</span><span class="sxs-lookup"><span data-stu-id="5a16c-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="5a16c-113">Protože SqlMetal je nástroj příkazového řádku, můžete ho použít v procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="5a16c-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="5a16c-114">Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="5a16c-114">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="5a16c-115">Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md). Na příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5a16c-115">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a16c-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a16c-116">Syntax</span></span>  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="5a16c-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5a16c-117">Options</span></span>  
 <span data-ttu-id="5a16c-118">Chcete-li zobrazit aktuální seznam možnost, zadejte `sqlmetal /?` na příkazovém řádku z umístění instalace.</span><span class="sxs-lookup"><span data-stu-id="5a16c-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="5a16c-119">**Možnosti připojení**</span><span class="sxs-lookup"><span data-stu-id="5a16c-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="5a16c-120">Možnost</span><span class="sxs-lookup"><span data-stu-id="5a16c-120">Option</span></span>|<span data-ttu-id="5a16c-121">Popis</span><span class="sxs-lookup"><span data-stu-id="5a16c-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5a16c-122">**/ Server:**  *\<name >*</span><span class="sxs-lookup"><span data-stu-id="5a16c-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="5a16c-123">Určuje název databázového serveru.</span><span class="sxs-lookup"><span data-stu-id="5a16c-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="5a16c-124">**/ databáze:**  *\<name >*</span><span class="sxs-lookup"><span data-stu-id="5a16c-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="5a16c-125">Určuje katalog databází na serveru.</span><span class="sxs-lookup"><span data-stu-id="5a16c-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="5a16c-126">**Parametr/user:**  *\<name >*</span><span class="sxs-lookup"><span data-stu-id="5a16c-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="5a16c-127">Určuje přihlašovací jméno uživatele. Výchozí hodnota: Použít ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5a16c-127">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="5a16c-128">**/ Password:**  *\<heslo >*</span><span class="sxs-lookup"><span data-stu-id="5a16c-128">**/password:** *\<password>*</span></span>|<span data-ttu-id="5a16c-129">Určuje heslo pro přihlášení.</span><span class="sxs-lookup"><span data-stu-id="5a16c-129">Specifies logon password.</span></span> <span data-ttu-id="5a16c-130">Výchozí hodnota: Použít ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5a16c-130">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="5a16c-131">**/ kontext:**  *\<připojovací řetězec >*</span><span class="sxs-lookup"><span data-stu-id="5a16c-131">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="5a16c-132">Určuje připojovací řetězec databáze.</span><span class="sxs-lookup"><span data-stu-id="5a16c-132">Specifies database connection string.</span></span> <span data-ttu-id="5a16c-133">Nelze použít s **/server**, **/databáze**, **User**, nebo **/Password** možnosti.</span><span class="sxs-lookup"><span data-stu-id="5a16c-133">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="5a16c-134">Nezahrnujte název souboru do připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="5a16c-134">Do not include the file name in the connection string.</span></span> <span data-ttu-id="5a16c-135">Místo toho přidejte název souboru do příkazového řádku jako vstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="5a16c-135">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="5a16c-136">Například následující řádek určuje "c:\northwnd.mdf" jako vstupní soubor: **/code:"c:\northwind.cs na sqlmetal" /language:csharp "c:\northwnd.mdf"**.</span><span class="sxs-lookup"><span data-stu-id="5a16c-136">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="5a16c-137">**/ timeout:**  *\<sekund >*</span><span class="sxs-lookup"><span data-stu-id="5a16c-137">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="5a16c-138">Určuje hodnotu časového limitu při přístupu SqlMetal k databázi.</span><span class="sxs-lookup"><span data-stu-id="5a16c-138">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="5a16c-139">Výchozí hodnota: 0 (to znamená žádný časový limit).</span><span class="sxs-lookup"><span data-stu-id="5a16c-139">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="5a16c-140">**Možnosti extrakce**</span><span class="sxs-lookup"><span data-stu-id="5a16c-140">**Extraction options**</span></span>  
  
|<span data-ttu-id="5a16c-141">Možnost</span><span class="sxs-lookup"><span data-stu-id="5a16c-141">Option</span></span>|<span data-ttu-id="5a16c-142">Popis</span><span class="sxs-lookup"><span data-stu-id="5a16c-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5a16c-143">**/Views**</span><span class="sxs-lookup"><span data-stu-id="5a16c-143">**/views**</span></span>|<span data-ttu-id="5a16c-144">Extrahuje zobrazení databáze.</span><span class="sxs-lookup"><span data-stu-id="5a16c-144">Extracts database views.</span></span>|  
|<span data-ttu-id="5a16c-145">**/functions**</span><span class="sxs-lookup"><span data-stu-id="5a16c-145">**/functions**</span></span>|<span data-ttu-id="5a16c-146">Extrahuje funkce databáze.</span><span class="sxs-lookup"><span data-stu-id="5a16c-146">Extracts database functions.</span></span>|  
|<span data-ttu-id="5a16c-147">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="5a16c-147">**/sprocs**</span></span>|<span data-ttu-id="5a16c-148">Extrahuje uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="5a16c-148">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="5a16c-149">**Možnosti výstupu**</span><span class="sxs-lookup"><span data-stu-id="5a16c-149">**Output options**</span></span>  
  
|<span data-ttu-id="5a16c-150">Možnost</span><span class="sxs-lookup"><span data-stu-id="5a16c-150">Option</span></span>|<span data-ttu-id="5a16c-151">Popis</span><span class="sxs-lookup"><span data-stu-id="5a16c-151">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5a16c-152">**/dbml** *[: soubor]*</span><span class="sxs-lookup"><span data-stu-id="5a16c-152">**/dbml** *[:file]*</span></span>|<span data-ttu-id="5a16c-153">Odešle výstup jako .dbml.</span><span class="sxs-lookup"><span data-stu-id="5a16c-153">Sends output as .dbml.</span></span> <span data-ttu-id="5a16c-154">Nelze použít s **/map** možnost.</span><span class="sxs-lookup"><span data-stu-id="5a16c-154">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="5a16c-155">**/ kódu** *[: soubor]*</span><span class="sxs-lookup"><span data-stu-id="5a16c-155">**/code** *[:file]*</span></span>|<span data-ttu-id="5a16c-156">Odešle výstup jako zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="5a16c-156">Sends output as source code.</span></span> <span data-ttu-id="5a16c-157">Nelze použít s **/dbml** možnost.</span><span class="sxs-lookup"><span data-stu-id="5a16c-157">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="5a16c-158">**/ map** *[: soubor]*</span><span class="sxs-lookup"><span data-stu-id="5a16c-158">**/map** *[:file]*</span></span>|<span data-ttu-id="5a16c-159">Generuje soubor mapování XML namísto atributů.</span><span class="sxs-lookup"><span data-stu-id="5a16c-159">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="5a16c-160">Nelze použít s **/dbml** možnost.</span><span class="sxs-lookup"><span data-stu-id="5a16c-160">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="5a16c-161">**Různé**</span><span class="sxs-lookup"><span data-stu-id="5a16c-161">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="5a16c-162">Možnost</span><span class="sxs-lookup"><span data-stu-id="5a16c-162">Option</span></span>|<span data-ttu-id="5a16c-163">Popis</span><span class="sxs-lookup"><span data-stu-id="5a16c-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5a16c-164">**/Language:**  *\<jazyka >*</span><span class="sxs-lookup"><span data-stu-id="5a16c-164">**/language:** *\<language>*</span></span>|<span data-ttu-id="5a16c-165">Určuje jazyk zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="5a16c-165">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="5a16c-166">Platný  *\<jazyk >*: vb, csharp.</span><span class="sxs-lookup"><span data-stu-id="5a16c-166">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="5a16c-167">Výchozí hodnota: Odvozeno z přípony názvu souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="5a16c-167">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="5a16c-168">**/ NAMESPACE:**  *\<name >*</span><span class="sxs-lookup"><span data-stu-id="5a16c-168">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="5a16c-169">Určuje obor názvů generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5a16c-169">Specifies namespace of the generated code.</span></span> <span data-ttu-id="5a16c-170">Výchozí hodnota: Žádný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="5a16c-170">Default value: no namespace.</span></span>|  
|<span data-ttu-id="5a16c-171">**/ Context:**  *\<typ >*</span><span class="sxs-lookup"><span data-stu-id="5a16c-171">**/context:** *\<type>*</span></span>|<span data-ttu-id="5a16c-172">Určuje název třídy datového kontextu.</span><span class="sxs-lookup"><span data-stu-id="5a16c-172">Specifies name of data context class.</span></span> <span data-ttu-id="5a16c-173">Výchozí hodnota: Odvozen od názvu databáze.</span><span class="sxs-lookup"><span data-stu-id="5a16c-173">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="5a16c-174">**/entitybase:**  *\<typ >*</span><span class="sxs-lookup"><span data-stu-id="5a16c-174">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="5a16c-175">Určuje základní třídu z tříd entit v generovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="5a16c-175">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="5a16c-176">Výchozí hodnota: Entity nemají žádnou základní třídu.</span><span class="sxs-lookup"><span data-stu-id="5a16c-176">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="5a16c-177">**/ pluralizovat**</span><span class="sxs-lookup"><span data-stu-id="5a16c-177">**/pluralize**</span></span>|<span data-ttu-id="5a16c-178">Automaticky převádí názvy tříd a členů do množného nebo jednotného čísla.</span><span class="sxs-lookup"><span data-stu-id="5a16c-178">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="5a16c-179">Tato možnost je dostupná pouze v USA Anglickou verzi.</span><span class="sxs-lookup"><span data-stu-id="5a16c-179">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="5a16c-180">**/Serialization:**  *\<možnost >*</span><span class="sxs-lookup"><span data-stu-id="5a16c-180">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="5a16c-181">Generuje serializovatelné třídy.</span><span class="sxs-lookup"><span data-stu-id="5a16c-181">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="5a16c-182">Platný  *\<možnost >*: None, Unidirectional.</span><span class="sxs-lookup"><span data-stu-id="5a16c-182">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="5a16c-183">Výchozí hodnota: Žádný.</span><span class="sxs-lookup"><span data-stu-id="5a16c-183">Default value: None.</span></span><br /><br /> <span data-ttu-id="5a16c-184">Další informace najdete v tématu [serializace](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="5a16c-184">For more information, see [Serialization](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="5a16c-185">**Vstupní soubor**</span><span class="sxs-lookup"><span data-stu-id="5a16c-185">**Input File**</span></span>  
  
|<span data-ttu-id="5a16c-186">Možnost</span><span class="sxs-lookup"><span data-stu-id="5a16c-186">Option</span></span>|<span data-ttu-id="5a16c-187">Popis</span><span class="sxs-lookup"><span data-stu-id="5a16c-187">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5a16c-188">**\<vstupní soubor >**</span><span class="sxs-lookup"><span data-stu-id="5a16c-188">**\<input file>**</span></span>|<span data-ttu-id="5a16c-189">Určuje soubor MDF systému SQL Server Express [!INCLUDE[ssEW](../../../includes/ssew-md.md)] soubor SDF nebo dbml pomocný soubor.</span><span class="sxs-lookup"><span data-stu-id="5a16c-189">Specifies a SQL Server Express .mdf file, a [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a16c-190">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a16c-190">Remarks</span></span>  
 <span data-ttu-id="5a16c-191">Funkce SqlMetal ve skutečnosti probíhá ve dvou krocích:</span><span class="sxs-lookup"><span data-stu-id="5a16c-191">SqlMetal functionality actually involves two steps:</span></span>  
  
-   <span data-ttu-id="5a16c-192">Extrahování metadat databáze do souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="5a16c-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
-   <span data-ttu-id="5a16c-193">Generování výstupního souboru s kódem.</span><span class="sxs-lookup"><span data-stu-id="5a16c-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="5a16c-194">Pomocí možnosti příkazového řádku, můžete vytvořit [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] nebo zdrojového kódu C#, nebo můžete vytvořit mapování souboru XML.</span><span class="sxs-lookup"><span data-stu-id="5a16c-194">By using the appropriate command-line options, you can produce [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="5a16c-195">Chcete-li extrahovat metadata ze souboru .mdf, musíte zadat název souboru .mdf za všemi ostatními možnostmi.</span><span class="sxs-lookup"><span data-stu-id="5a16c-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="5a16c-196">Pokud žádné **/server** není zadaný, **localhost nebo sqlexpress** se předpokládá.</span><span class="sxs-lookup"><span data-stu-id="5a16c-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 [!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)]<span data-ttu-id="5a16c-197">Pokud jeden nebo více z následujících podmínek jsou splněny, vyvolá výjimku:</span><span class="sxs-lookup"><span data-stu-id="5a16c-197"> throws an exception if one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="5a16c-198">SqlMetal se pokusí extrahovat uloženou proceduru, která volá sama sebe.</span><span class="sxs-lookup"><span data-stu-id="5a16c-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
-   <span data-ttu-id="5a16c-199">Úroveň vnoření uložené procedury, funkce nebo zobrazení je vyšší než 32.</span><span class="sxs-lookup"><span data-stu-id="5a16c-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="5a16c-200">SqlMetal tuto výjimku zachytí a ohlásí ji jako varování.</span><span class="sxs-lookup"><span data-stu-id="5a16c-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="5a16c-201">Chcete-li zadat název vstupního souboru, přidejte název souboru do příkazového řádku jako vstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="5a16c-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="5a16c-202">Včetně názvu souboru v připojovacím řetězci (pomocí **/kontext** možnost) není podporován.</span><span class="sxs-lookup"><span data-stu-id="5a16c-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5a16c-203">Příklady</span><span class="sxs-lookup"><span data-stu-id="5a16c-203">Examples</span></span>  
 <span data-ttu-id="5a16c-204">Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL:</span><span class="sxs-lookup"><span data-stu-id="5a16c-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="5a16c-205">**SqlMetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="5a16c-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="5a16c-206">Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL ze souboru .mdf pomocí SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="5a16c-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="5a16c-207">**SqlMetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="5a16c-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="5a16c-208">Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL z SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="5a16c-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="5a16c-209">**SqlMetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="5a16c-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="5a16c-210">Vygenerování zdrojového kódu ze souboru metadat .dbml:</span><span class="sxs-lookup"><span data-stu-id="5a16c-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="5a16c-211">**SqlMetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="5a16c-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="5a16c-212">Vygenerování zdrojového kódu přímo z metadat SQL:</span><span class="sxs-lookup"><span data-stu-id="5a16c-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="5a16c-213">**SqlMetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="5a16c-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a16c-214">Při použití **/ pluralizovat** možnost s ukázková databáze Northwind, Všimněte si následujícího chování.</span><span class="sxs-lookup"><span data-stu-id="5a16c-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="5a16c-215">Když SqlMetal vytváří názvy řádků pro tabulky, názvy tabulek jsou v jednotném čísle.</span><span class="sxs-lookup"><span data-stu-id="5a16c-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="5a16c-216">Když umožňuje <xref:System.Data.Linq.DataContext> vlastnosti pro tabulky, názvy tabulek jsou množném čísle.</span><span class="sxs-lookup"><span data-stu-id="5a16c-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="5a16c-217">Tabulky v ukázkové databázi Northwind jsou shodou okolností již v množném čísle.</span><span class="sxs-lookup"><span data-stu-id="5a16c-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="5a16c-218">Proto neuvidíte, jak tato část funguje.</span><span class="sxs-lookup"><span data-stu-id="5a16c-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="5a16c-219">Přestože jsou názvy tabulek databáze zpravidla zapisovány v jednotném čísle, v rozhraní .NET je rovněž obvyklé pojmenovávání kolekcí v množném čísle.</span><span class="sxs-lookup"><span data-stu-id="5a16c-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a16c-220">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a16c-220">See Also</span></span>  
 [<span data-ttu-id="5a16c-221">Postupy: Generování objektového modelu v jazyce Visual Basic nebo C#</span><span class="sxs-lookup"><span data-stu-id="5a16c-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 [<span data-ttu-id="5a16c-222">Generování kódu v LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5a16c-222">Code Generation in LINQ to SQL</span></span>](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="5a16c-223">Externí mapování</span><span class="sxs-lookup"><span data-stu-id="5a16c-223">External Mapping</span></span>](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
