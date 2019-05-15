---
title: SqlMetal.exe (nástroj pro vytváření kódu)
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: b6f7450b4f682ea5ac69fd1bab434b27451e58df
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586064"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="ca99b-102">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="ca99b-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="ca99b-103">Nástroj příkazového řádku SqlMetal generuje kód a mapování pro [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] součásti rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca99b-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="ca99b-104">Použitím možností uvedených dále v tomto tématu můžete dát nástroji SqlMetal pokyn, aby provedl několik různých úkonů, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="ca99b-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="ca99b-105">Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování z databáze.</span><span class="sxs-lookup"><span data-stu-id="ca99b-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="ca99b-106">Vygenerování přechodného souboru .dbml (database markup language) z databáze za účelem přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="ca99b-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="ca99b-107">Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování ze souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="ca99b-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="ca99b-108">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca99b-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="ca99b-109">Ve výchozím nastavení, se nachází v souboru `drive`: \Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span><span class="sxs-lookup"><span data-stu-id="ca99b-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="ca99b-110">Pokud nenainstalujete sady Visual Studio, můžete také si soubor SQLMetal Stáhnout [sady Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span><span class="sxs-lookup"><span data-stu-id="ca99b-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca99b-111">Vývojáři, kteří používají Visual Studio můžete také použít [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] k vytvoření tříd entit.</span><span class="sxs-lookup"><span data-stu-id="ca99b-111">Developers who use Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] to generate entity classes.</span></span> <span data-ttu-id="ca99b-112">Metoda využívající příkazový řádek je vhodná u velkých databází.</span><span class="sxs-lookup"><span data-stu-id="ca99b-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="ca99b-113">Protože SqlMetal je nástroj příkazového řádku, můžete ho použít v procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca99b-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="ca99b-114">Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7).</span><span class="sxs-lookup"><span data-stu-id="ca99b-114">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="ca99b-115">Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md). Na příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="ca99b-115">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca99b-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca99b-116">Syntax</span></span>  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="ca99b-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ca99b-117">Options</span></span>  
 <span data-ttu-id="ca99b-118">Pokud chcete zobrazit aktuální seznam možností, zadejte `sqlmetal /?` příkazového řádku z umístění instalace.</span><span class="sxs-lookup"><span data-stu-id="ca99b-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="ca99b-119">**Možnosti připojení**</span><span class="sxs-lookup"><span data-stu-id="ca99b-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="ca99b-120">Možnost</span><span class="sxs-lookup"><span data-stu-id="ca99b-120">Option</span></span>|<span data-ttu-id="ca99b-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ca99b-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ca99b-122">**/ Server:**  *\<name >*</span><span class="sxs-lookup"><span data-stu-id="ca99b-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="ca99b-123">Určuje název databázového serveru.</span><span class="sxs-lookup"><span data-stu-id="ca99b-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="ca99b-124">**/ databáze:**  *\<name >*</span><span class="sxs-lookup"><span data-stu-id="ca99b-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="ca99b-125">Určuje katalog databází na serveru.</span><span class="sxs-lookup"><span data-stu-id="ca99b-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="ca99b-126">**/ user:**  *\<name >*</span><span class="sxs-lookup"><span data-stu-id="ca99b-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="ca99b-127">Určuje přihlašovací jméno uživatele. Výchozí hodnota: Použijte ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="ca99b-127">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="ca99b-128">**/password:** *\<password>*</span><span class="sxs-lookup"><span data-stu-id="ca99b-128">**/password:** *\<password>*</span></span>|<span data-ttu-id="ca99b-129">Určuje heslo pro přihlášení.</span><span class="sxs-lookup"><span data-stu-id="ca99b-129">Specifies logon password.</span></span> <span data-ttu-id="ca99b-130">Výchozí hodnota: Použijte ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="ca99b-130">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="ca99b-131">**/ conn:**  *\<připojovací řetězec >*</span><span class="sxs-lookup"><span data-stu-id="ca99b-131">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="ca99b-132">Určuje připojovací řetězec databáze.</span><span class="sxs-lookup"><span data-stu-id="ca99b-132">Specifies database connection string.</span></span> <span data-ttu-id="ca99b-133">Nelze použít s **/server**, **/database**, **/User**, nebo **/Password** možnosti.</span><span class="sxs-lookup"><span data-stu-id="ca99b-133">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="ca99b-134">Nezahrnujte název souboru do připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="ca99b-134">Do not include the file name in the connection string.</span></span> <span data-ttu-id="ca99b-135">Místo toho přidejte název souboru do příkazového řádku jako vstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="ca99b-135">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="ca99b-136">Například následující řádek určuje "c:\northwnd.mdf" jako vstupní soubor: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span><span class="sxs-lookup"><span data-stu-id="ca99b-136">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="ca99b-137">**/ timeout:**  *\<sekund >*</span><span class="sxs-lookup"><span data-stu-id="ca99b-137">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="ca99b-138">Určuje hodnotu časového limitu při přístupu SqlMetal k databázi.</span><span class="sxs-lookup"><span data-stu-id="ca99b-138">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="ca99b-139">Výchozí hodnota: 0 (to znamená žádný časový limit).</span><span class="sxs-lookup"><span data-stu-id="ca99b-139">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="ca99b-140">**Možnosti extrahování**</span><span class="sxs-lookup"><span data-stu-id="ca99b-140">**Extraction options**</span></span>  
  
|<span data-ttu-id="ca99b-141">Možnost</span><span class="sxs-lookup"><span data-stu-id="ca99b-141">Option</span></span>|<span data-ttu-id="ca99b-142">Popis</span><span class="sxs-lookup"><span data-stu-id="ca99b-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ca99b-143">**/Views**</span><span class="sxs-lookup"><span data-stu-id="ca99b-143">**/views**</span></span>|<span data-ttu-id="ca99b-144">Extrahuje zobrazení databáze.</span><span class="sxs-lookup"><span data-stu-id="ca99b-144">Extracts database views.</span></span>|  
|<span data-ttu-id="ca99b-145">**/functions**</span><span class="sxs-lookup"><span data-stu-id="ca99b-145">**/functions**</span></span>|<span data-ttu-id="ca99b-146">Extrahuje funkce databáze.</span><span class="sxs-lookup"><span data-stu-id="ca99b-146">Extracts database functions.</span></span>|  
|<span data-ttu-id="ca99b-147">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="ca99b-147">**/sprocs**</span></span>|<span data-ttu-id="ca99b-148">Extrahuje uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="ca99b-148">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="ca99b-149">**Možnosti výstupu**</span><span class="sxs-lookup"><span data-stu-id="ca99b-149">**Output options**</span></span>  
  
|<span data-ttu-id="ca99b-150">Možnost</span><span class="sxs-lookup"><span data-stu-id="ca99b-150">Option</span></span>|<span data-ttu-id="ca99b-151">Popis</span><span class="sxs-lookup"><span data-stu-id="ca99b-151">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ca99b-152">**/dbml** *[: file]*</span><span class="sxs-lookup"><span data-stu-id="ca99b-152">**/dbml** *[:file]*</span></span>|<span data-ttu-id="ca99b-153">Odešle výstup jako .dbml.</span><span class="sxs-lookup"><span data-stu-id="ca99b-153">Sends output as .dbml.</span></span> <span data-ttu-id="ca99b-154">Nelze použít s **/map** možnost.</span><span class="sxs-lookup"><span data-stu-id="ca99b-154">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="ca99b-155">**/ code** *[: file]*</span><span class="sxs-lookup"><span data-stu-id="ca99b-155">**/code** *[:file]*</span></span>|<span data-ttu-id="ca99b-156">Odešle výstup jako zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="ca99b-156">Sends output as source code.</span></span> <span data-ttu-id="ca99b-157">Nelze použít s **/dbml** možnost.</span><span class="sxs-lookup"><span data-stu-id="ca99b-157">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="ca99b-158">**/ map** *[: file]*</span><span class="sxs-lookup"><span data-stu-id="ca99b-158">**/map** *[:file]*</span></span>|<span data-ttu-id="ca99b-159">Generuje soubor mapování XML namísto atributů.</span><span class="sxs-lookup"><span data-stu-id="ca99b-159">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="ca99b-160">Nelze použít s **/dbml** možnost.</span><span class="sxs-lookup"><span data-stu-id="ca99b-160">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="ca99b-161">**Různé**</span><span class="sxs-lookup"><span data-stu-id="ca99b-161">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="ca99b-162">Možnost</span><span class="sxs-lookup"><span data-stu-id="ca99b-162">Option</span></span>|<span data-ttu-id="ca99b-163">Popis</span><span class="sxs-lookup"><span data-stu-id="ca99b-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ca99b-164">**/Language:**  *\<jazyk >*</span><span class="sxs-lookup"><span data-stu-id="ca99b-164">**/language:** *\<language>*</span></span>|<span data-ttu-id="ca99b-165">Určuje jazyk zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="ca99b-165">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="ca99b-166">Platný  *\<jazyk >*: vb, csharp.</span><span class="sxs-lookup"><span data-stu-id="ca99b-166">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="ca99b-167">Výchozí hodnota: Odvozeno z přípony názvu souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="ca99b-167">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="ca99b-168">**/ NAMESPACE:**  *\<name >*</span><span class="sxs-lookup"><span data-stu-id="ca99b-168">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="ca99b-169">Určuje obor názvů generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ca99b-169">Specifies namespace of the generated code.</span></span> <span data-ttu-id="ca99b-170">Výchozí hodnota: Žádný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ca99b-170">Default value: no namespace.</span></span>|  
|<span data-ttu-id="ca99b-171">**/ Context:**  *\<typ >*</span><span class="sxs-lookup"><span data-stu-id="ca99b-171">**/context:** *\<type>*</span></span>|<span data-ttu-id="ca99b-172">Určuje název třídy datového kontextu.</span><span class="sxs-lookup"><span data-stu-id="ca99b-172">Specifies name of data context class.</span></span> <span data-ttu-id="ca99b-173">Výchozí hodnota: Odvozený od názvu databáze.</span><span class="sxs-lookup"><span data-stu-id="ca99b-173">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="ca99b-174">**/entitybase:**  *\<typ >*</span><span class="sxs-lookup"><span data-stu-id="ca99b-174">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="ca99b-175">Určuje základní třídu z tříd entit v generovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="ca99b-175">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="ca99b-176">Výchozí hodnota: Entity nemají žádnou základní třídu.</span><span class="sxs-lookup"><span data-stu-id="ca99b-176">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="ca99b-177">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="ca99b-177">**/pluralize**</span></span>|<span data-ttu-id="ca99b-178">Automaticky převádí názvy tříd a členů do množného nebo jednotného čísla.</span><span class="sxs-lookup"><span data-stu-id="ca99b-178">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="ca99b-179">Tato možnost je dostupná jenom v USA. Anglickou verzi.</span><span class="sxs-lookup"><span data-stu-id="ca99b-179">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="ca99b-180">**/Serialization:**  *\<možnost >*</span><span class="sxs-lookup"><span data-stu-id="ca99b-180">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="ca99b-181">Generuje serializovatelné třídy.</span><span class="sxs-lookup"><span data-stu-id="ca99b-181">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="ca99b-182">Platný  *\<možnost >*: Žádný, jednosměrný.</span><span class="sxs-lookup"><span data-stu-id="ca99b-182">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="ca99b-183">Výchozí hodnota: Žádné</span><span class="sxs-lookup"><span data-stu-id="ca99b-183">Default value: None.</span></span><br /><br /> <span data-ttu-id="ca99b-184">Další informace najdete v tématu [serializace](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="ca99b-184">For more information, see [Serialization](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="ca99b-185">**Vstupní soubor**</span><span class="sxs-lookup"><span data-stu-id="ca99b-185">**Input File**</span></span>  
  
|<span data-ttu-id="ca99b-186">Možnost</span><span class="sxs-lookup"><span data-stu-id="ca99b-186">Option</span></span>|<span data-ttu-id="ca99b-187">Popis</span><span class="sxs-lookup"><span data-stu-id="ca99b-187">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ca99b-188">**\<vstupní soubor >**</span><span class="sxs-lookup"><span data-stu-id="ca99b-188">**\<input file>**</span></span>|<span data-ttu-id="ca99b-189">Určuje soubor .mdf serveru SQL Server Express [!INCLUDE[ssEW](../../../includes/ssew-md.md)] soubor SDF nebo přechodný soubor .dbml.</span><span class="sxs-lookup"><span data-stu-id="ca99b-189">Specifies a SQL Server Express .mdf file, a [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca99b-190">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca99b-190">Remarks</span></span>  
 <span data-ttu-id="ca99b-191">Funkce SqlMetal ve skutečnosti probíhá ve dvou krocích:</span><span class="sxs-lookup"><span data-stu-id="ca99b-191">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="ca99b-192">Extrahování metadat databáze do souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="ca99b-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="ca99b-193">Generování výstupního souboru s kódem.</span><span class="sxs-lookup"><span data-stu-id="ca99b-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="ca99b-194">Pomocí vhodných možností příkazového řádku můžete vytvářet zdrojový kód jazyka Visual Basic nebo C#, nebo můžete vytvořit soubor mapování XML.</span><span class="sxs-lookup"><span data-stu-id="ca99b-194">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="ca99b-195">Chcete-li extrahovat metadata ze souboru .mdf, musíte zadat název souboru .mdf za všemi ostatními možnostmi.</span><span class="sxs-lookup"><span data-stu-id="ca99b-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="ca99b-196">Pokud ne **/server** není zadána, **localhost/sqlexpress** se předpokládá, že.</span><span class="sxs-lookup"><span data-stu-id="ca99b-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 [!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)] <span data-ttu-id="ca99b-197">vyvolá výjimku, pokud platí jedna nebo více z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="ca99b-197">throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="ca99b-198">SqlMetal se pokusí extrahovat uloženou proceduru, která volá sama sebe.</span><span class="sxs-lookup"><span data-stu-id="ca99b-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="ca99b-199">Úroveň vnoření uložené procedury, funkce nebo zobrazení je vyšší než 32.</span><span class="sxs-lookup"><span data-stu-id="ca99b-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="ca99b-200">SqlMetal tuto výjimku zachytí a ohlásí ji jako varování.</span><span class="sxs-lookup"><span data-stu-id="ca99b-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="ca99b-201">Chcete-li zadat název vstupního souboru, přidejte název souboru do příkazového řádku jako vstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="ca99b-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="ca99b-202">Včetně názvu souboru do připojovacího řetězce (pomocí **/conn** možnost) se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="ca99b-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ca99b-203">Příklady</span><span class="sxs-lookup"><span data-stu-id="ca99b-203">Examples</span></span>  
 <span data-ttu-id="ca99b-204">Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL:</span><span class="sxs-lookup"><span data-stu-id="ca99b-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="ca99b-205">**SqlMetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="ca99b-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="ca99b-206">Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL ze souboru .mdf pomocí SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="ca99b-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="ca99b-207">**SqlMetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="ca99b-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="ca99b-208">Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL z SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="ca99b-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="ca99b-209">**SqlMetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="ca99b-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="ca99b-210">Vygenerování zdrojového kódu ze souboru metadat .dbml:</span><span class="sxs-lookup"><span data-stu-id="ca99b-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="ca99b-211">**SqlMetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="ca99b-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="ca99b-212">Vygenerování zdrojového kódu přímo z metadat SQL:</span><span class="sxs-lookup"><span data-stu-id="ca99b-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="ca99b-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="ca99b-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca99b-214">Při použití **/ pluralize** možnost s ukázkovou databází Northwind, pamatujte na následující chování.</span><span class="sxs-lookup"><span data-stu-id="ca99b-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="ca99b-215">Když SqlMetal vytváří názvy řádků pro tabulky, názvy tabulek jsou v jednotném čísle.</span><span class="sxs-lookup"><span data-stu-id="ca99b-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="ca99b-216">Který je <xref:System.Data.Linq.DataContext> vlastnosti pro tabulky, názvy tabulek jsou v množném čísle.</span><span class="sxs-lookup"><span data-stu-id="ca99b-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="ca99b-217">Tabulky v ukázkové databázi Northwind jsou shodou okolností již v množném čísle.</span><span class="sxs-lookup"><span data-stu-id="ca99b-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="ca99b-218">Proto neuvidíte, jak tato část funguje.</span><span class="sxs-lookup"><span data-stu-id="ca99b-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="ca99b-219">Přestože jsou názvy tabulek databáze zpravidla zapisovány v jednotném čísle, v rozhraní .NET je rovněž obvyklé pojmenovávání kolekcí v množném čísle.</span><span class="sxs-lookup"><span data-stu-id="ca99b-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca99b-220">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca99b-220">See also</span></span>

- [<span data-ttu-id="ca99b-221">Postupy: Generování objektového modelu v jazyce Visual Basic neboC#</span><span class="sxs-lookup"><span data-stu-id="ca99b-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="ca99b-222">Generování kódu v LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ca99b-222">Code Generation in LINQ to SQL</span></span>](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="ca99b-223">Externí mapování</span><span class="sxs-lookup"><span data-stu-id="ca99b-223">External Mapping</span></span>](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
