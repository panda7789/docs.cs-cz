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
ms.openlocfilehash: 0d12196acab5a50f7dd6fc78e6dccc098cf3e2de
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894605"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="25e28-102">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="25e28-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="25e28-103">Nástroj příkazového řádku SQLMetal generuje kód a mapování pro [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] komponentu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="25e28-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="25e28-104">Použitím možností uvedených dále v tomto tématu můžete dát nástroji SqlMetal pokyn, aby provedl několik různých úkonů, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="25e28-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="25e28-105">Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování z databáze.</span><span class="sxs-lookup"><span data-stu-id="25e28-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="25e28-106">Vygenerování přechodného souboru .dbml (database markup language) z databáze za účelem přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="25e28-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="25e28-107">Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování ze souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="25e28-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="25e28-108">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="25e28-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="25e28-109">Ve výchozím nastavení se soubor nachází v `drive`umístění: \Program Files\Microsoft SDKs\Windows\v \Bin.`n.nn`</span><span class="sxs-lookup"><span data-stu-id="25e28-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="25e28-110">Pokud nenainstalujete aplikaci Visual Studio, můžete také získat soubor SQLMetal stažením [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span><span class="sxs-lookup"><span data-stu-id="25e28-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25e28-111">Vývojáři, kteří používají Visual Studio, mohou také použít Návrhář relací objektů k vygenerování tříd entit.</span><span class="sxs-lookup"><span data-stu-id="25e28-111">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="25e28-112">Metoda využívající příkazový řádek je vhodná u velkých databází.</span><span class="sxs-lookup"><span data-stu-id="25e28-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="25e28-113">Protože SqlMetal je nástroj příkazového řádku, můžete ho použít v procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="25e28-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="25e28-114">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="25e28-114">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="25e28-115">Další informace najdete v tématu [výzvy k zadání příkazu](../../../docs/framework/tools/developer-command-prompt-for-vs.md). Na příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="25e28-115">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25e28-116">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25e28-116">Syntax</span></span>  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="25e28-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="25e28-117">Options</span></span>  
 <span data-ttu-id="25e28-118">Chcete-li zobrazit nejaktuálnější seznam možností, zadejte `sqlmetal /?` do příkazového řádku z nainstalovaného umístění.</span><span class="sxs-lookup"><span data-stu-id="25e28-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="25e28-119">**Možnosti připojení**</span><span class="sxs-lookup"><span data-stu-id="25e28-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="25e28-120">Možnost</span><span class="sxs-lookup"><span data-stu-id="25e28-120">Option</span></span>|<span data-ttu-id="25e28-121">Popis</span><span class="sxs-lookup"><span data-stu-id="25e28-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="25e28-122">**/Server:**  *název\<>*</span><span class="sxs-lookup"><span data-stu-id="25e28-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="25e28-123">Určuje název databázového serveru.</span><span class="sxs-lookup"><span data-stu-id="25e28-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="25e28-124">**/Database:**  *název\<>*</span><span class="sxs-lookup"><span data-stu-id="25e28-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="25e28-125">Určuje katalog databází na serveru.</span><span class="sxs-lookup"><span data-stu-id="25e28-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="25e28-126">**/User:**  *název\<>*</span><span class="sxs-lookup"><span data-stu-id="25e28-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="25e28-127">Určuje přihlašovací jméno uživatele. Výchozí hodnota: Použijte ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="25e28-127">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="25e28-128">**/Password:**  *>\<hesla*</span><span class="sxs-lookup"><span data-stu-id="25e28-128">**/password:** *\<password>*</span></span>|<span data-ttu-id="25e28-129">Určuje heslo pro přihlášení.</span><span class="sxs-lookup"><span data-stu-id="25e28-129">Specifies logon password.</span></span> <span data-ttu-id="25e28-130">Výchozí hodnota: Použijte ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="25e28-130">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="25e28-131">**/Conn:** > připojovacího řetězce  *\<*</span><span class="sxs-lookup"><span data-stu-id="25e28-131">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="25e28-132">Určuje připojovací řetězec databáze.</span><span class="sxs-lookup"><span data-stu-id="25e28-132">Specifies database connection string.</span></span> <span data-ttu-id="25e28-133">Nelze použít s možnostmi **/Server**, **/Database**, **/User**nebo **/Password** .</span><span class="sxs-lookup"><span data-stu-id="25e28-133">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="25e28-134">Nezahrnujte název souboru do připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="25e28-134">Do not include the file name in the connection string.</span></span> <span data-ttu-id="25e28-135">Místo toho přidejte název souboru do příkazového řádku jako vstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="25e28-135">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="25e28-136">Například následující řádek určuje "c:\northwnd.mdf" jako vstupní soubor: **SQLMetal/Code: "c:\Northwind.cs"/Language: CSharp "c:\northwnd.mdf"** .</span><span class="sxs-lookup"><span data-stu-id="25e28-136">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="25e28-137">**/timeout:**  *>\<sekund*</span><span class="sxs-lookup"><span data-stu-id="25e28-137">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="25e28-138">Určuje hodnotu časového limitu při přístupu SqlMetal k databázi.</span><span class="sxs-lookup"><span data-stu-id="25e28-138">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="25e28-139">Výchozí hodnota: 0 (tj. žádný časový limit).</span><span class="sxs-lookup"><span data-stu-id="25e28-139">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="25e28-140">**Možnosti extrakce**</span><span class="sxs-lookup"><span data-stu-id="25e28-140">**Extraction options**</span></span>  
  
|<span data-ttu-id="25e28-141">Možnost</span><span class="sxs-lookup"><span data-stu-id="25e28-141">Option</span></span>|<span data-ttu-id="25e28-142">Popis</span><span class="sxs-lookup"><span data-stu-id="25e28-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="25e28-143">**/views**</span><span class="sxs-lookup"><span data-stu-id="25e28-143">**/views**</span></span>|<span data-ttu-id="25e28-144">Extrahuje zobrazení databáze.</span><span class="sxs-lookup"><span data-stu-id="25e28-144">Extracts database views.</span></span>|  
|<span data-ttu-id="25e28-145">**/functions**</span><span class="sxs-lookup"><span data-stu-id="25e28-145">**/functions**</span></span>|<span data-ttu-id="25e28-146">Extrahuje funkce databáze.</span><span class="sxs-lookup"><span data-stu-id="25e28-146">Extracts database functions.</span></span>|  
|<span data-ttu-id="25e28-147">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="25e28-147">**/sprocs**</span></span>|<span data-ttu-id="25e28-148">Extrahuje uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="25e28-148">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="25e28-149">**Možnosti výstupu**</span><span class="sxs-lookup"><span data-stu-id="25e28-149">**Output options**</span></span>  
  
|<span data-ttu-id="25e28-150">Možnost</span><span class="sxs-lookup"><span data-stu-id="25e28-150">Option</span></span>|<span data-ttu-id="25e28-151">Popis</span><span class="sxs-lookup"><span data-stu-id="25e28-151">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="25e28-152">**/dbml** *[: soubor]*</span><span class="sxs-lookup"><span data-stu-id="25e28-152">**/dbml** *[:file]*</span></span>|<span data-ttu-id="25e28-153">Odešle výstup jako .dbml.</span><span class="sxs-lookup"><span data-stu-id="25e28-153">Sends output as .dbml.</span></span> <span data-ttu-id="25e28-154">Nelze použít s možností **/map** .</span><span class="sxs-lookup"><span data-stu-id="25e28-154">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="25e28-155">**/Code** *[: soubor]*</span><span class="sxs-lookup"><span data-stu-id="25e28-155">**/code** *[:file]*</span></span>|<span data-ttu-id="25e28-156">Odešle výstup jako zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="25e28-156">Sends output as source code.</span></span> <span data-ttu-id="25e28-157">Nelze použít s možností **/dbml** .</span><span class="sxs-lookup"><span data-stu-id="25e28-157">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="25e28-158">**/map** *[: soubor]*</span><span class="sxs-lookup"><span data-stu-id="25e28-158">**/map** *[:file]*</span></span>|<span data-ttu-id="25e28-159">Generuje soubor mapování XML namísto atributů.</span><span class="sxs-lookup"><span data-stu-id="25e28-159">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="25e28-160">Nelze použít s možností **/dbml** .</span><span class="sxs-lookup"><span data-stu-id="25e28-160">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="25e28-161">**Různé**</span><span class="sxs-lookup"><span data-stu-id="25e28-161">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="25e28-162">Možnost</span><span class="sxs-lookup"><span data-stu-id="25e28-162">Option</span></span>|<span data-ttu-id="25e28-163">Popis</span><span class="sxs-lookup"><span data-stu-id="25e28-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="25e28-164">**/Language:**  *>\<jazyka*</span><span class="sxs-lookup"><span data-stu-id="25e28-164">**/language:** *\<language>*</span></span>|<span data-ttu-id="25e28-165">Určuje jazyk zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="25e28-165">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="25e28-166">*Platný\<jazyk >* : VB, CSharp.</span><span class="sxs-lookup"><span data-stu-id="25e28-166">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="25e28-167">Výchozí hodnota: Odvozeno z rozšíření názvu souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="25e28-167">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="25e28-168">**/Namespace:**  *název\<>*</span><span class="sxs-lookup"><span data-stu-id="25e28-168">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="25e28-169">Určuje obor názvů generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="25e28-169">Specifies namespace of the generated code.</span></span> <span data-ttu-id="25e28-170">Výchozí hodnota: Žádný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="25e28-170">Default value: no namespace.</span></span>|  
|<span data-ttu-id="25e28-171">**/Context:**  *Zadejte\<>*</span><span class="sxs-lookup"><span data-stu-id="25e28-171">**/context:** *\<type>*</span></span>|<span data-ttu-id="25e28-172">Určuje název třídy datového kontextu.</span><span class="sxs-lookup"><span data-stu-id="25e28-172">Specifies name of data context class.</span></span> <span data-ttu-id="25e28-173">Výchozí hodnota: Odvozeno z názvu databáze.</span><span class="sxs-lookup"><span data-stu-id="25e28-173">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="25e28-174">**/entitybase:**  *Zadejte\<>*</span><span class="sxs-lookup"><span data-stu-id="25e28-174">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="25e28-175">Určuje základní třídu z tříd entit v generovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="25e28-175">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="25e28-176">Výchozí hodnota: Entity nemají žádnou základní třídu.</span><span class="sxs-lookup"><span data-stu-id="25e28-176">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="25e28-177">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="25e28-177">**/pluralize**</span></span>|<span data-ttu-id="25e28-178">Automaticky převádí názvy tříd a členů do množného nebo jednotného čísla.</span><span class="sxs-lookup"><span data-stu-id="25e28-178">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="25e28-179">Tato možnost je dostupná jenom v USA. Anglická verze</span><span class="sxs-lookup"><span data-stu-id="25e28-179">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="25e28-180">**/Serialization:**  *možnost\<>*</span><span class="sxs-lookup"><span data-stu-id="25e28-180">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="25e28-181">Generuje serializovatelné třídy.</span><span class="sxs-lookup"><span data-stu-id="25e28-181">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="25e28-182">*Platná\<možnost >* : None, jednosměrný.</span><span class="sxs-lookup"><span data-stu-id="25e28-182">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="25e28-183">Výchozí hodnota: Žádné</span><span class="sxs-lookup"><span data-stu-id="25e28-183">Default value: None.</span></span><br /><br /> <span data-ttu-id="25e28-184">Další informace naleznete v tématu [serializace](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="25e28-184">For more information, see [Serialization](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="25e28-185">**Vstupní soubor**</span><span class="sxs-lookup"><span data-stu-id="25e28-185">**Input File**</span></span>  
  
|<span data-ttu-id="25e28-186">Možnost</span><span class="sxs-lookup"><span data-stu-id="25e28-186">Option</span></span>|<span data-ttu-id="25e28-187">Popis</span><span class="sxs-lookup"><span data-stu-id="25e28-187">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="25e28-188">**\<> vstupního souboru**</span><span class="sxs-lookup"><span data-stu-id="25e28-188">**\<input file>**</span></span>|<span data-ttu-id="25e28-189">Určuje SQL Server Express soubor. mdf, soubor SQL Server Compact 3,5. sdf nebo zprostředkující soubor. dbml.</span><span class="sxs-lookup"><span data-stu-id="25e28-189">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25e28-190">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25e28-190">Remarks</span></span>  
 <span data-ttu-id="25e28-191">Funkce SqlMetal ve skutečnosti probíhá ve dvou krocích:</span><span class="sxs-lookup"><span data-stu-id="25e28-191">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="25e28-192">Extrahování metadat databáze do souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="25e28-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="25e28-193">Generování výstupního souboru s kódem.</span><span class="sxs-lookup"><span data-stu-id="25e28-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="25e28-194">Pomocí příslušných možností příkazového řádku můžete vyvolat Visual Basic nebo C# zdrojový kód nebo můžete vystavit soubor mapování XML.</span><span class="sxs-lookup"><span data-stu-id="25e28-194">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="25e28-195">Chcete-li extrahovat metadata ze souboru .mdf, musíte zadat název souboru .mdf za všemi ostatními možnostmi.</span><span class="sxs-lookup"><span data-stu-id="25e28-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="25e28-196">Pokud se nezadá žádný **/Server** , předpokládá se **localhost/SQLEXPRESS** .</span><span class="sxs-lookup"><span data-stu-id="25e28-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="25e28-197">Microsoft SQL Server 2005 vyvolá výjimku, pokud je splněna jedna nebo více z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="25e28-197">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="25e28-198">SqlMetal se pokusí extrahovat uloženou proceduru, která volá sama sebe.</span><span class="sxs-lookup"><span data-stu-id="25e28-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="25e28-199">Úroveň vnoření uložené procedury, funkce nebo zobrazení je vyšší než 32.</span><span class="sxs-lookup"><span data-stu-id="25e28-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="25e28-200">SqlMetal tuto výjimku zachytí a ohlásí ji jako varování.</span><span class="sxs-lookup"><span data-stu-id="25e28-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="25e28-201">Chcete-li zadat název vstupního souboru, přidejte název souboru do příkazového řádku jako vstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="25e28-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="25e28-202">Zahrnutí názvu souboru do připojovacího řetězce (pomocí možnosti **/Conn** ) není podporováno.</span><span class="sxs-lookup"><span data-stu-id="25e28-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="25e28-203">Příklady</span><span class="sxs-lookup"><span data-stu-id="25e28-203">Examples</span></span>  
 <span data-ttu-id="25e28-204">Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL:</span><span class="sxs-lookup"><span data-stu-id="25e28-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="25e28-205">**SQLMetal/Server: MyServer/Database: Northwind/dbml: mymeta. dbml**</span><span class="sxs-lookup"><span data-stu-id="25e28-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="25e28-206">Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL ze souboru .mdf pomocí SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="25e28-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="25e28-207">**SQLMetal/dbml: mymeta. dbml mydbfile. mdf**</span><span class="sxs-lookup"><span data-stu-id="25e28-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="25e28-208">Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL z SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="25e28-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="25e28-209">**SQLMetal/Server: .\SQLEXPRESS/dbml: mymeta. dbml/Database: Northwind**</span><span class="sxs-lookup"><span data-stu-id="25e28-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="25e28-210">Vygenerování zdrojového kódu ze souboru metadat .dbml:</span><span class="sxs-lookup"><span data-stu-id="25e28-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="25e28-211">**SQLMetal/Namespace: NWIND/Code: NWIND. cs/Language: CSharp mymetal. dbml**</span><span class="sxs-lookup"><span data-stu-id="25e28-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="25e28-212">Vygenerování zdrojového kódu přímo z metadat SQL:</span><span class="sxs-lookup"><span data-stu-id="25e28-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="25e28-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="25e28-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25e28-214">Když použijete možnost **/pluralize** s ukázkovou databází Northwind, pamatujte na následující chování.</span><span class="sxs-lookup"><span data-stu-id="25e28-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="25e28-215">Když SqlMetal vytváří názvy řádků pro tabulky, názvy tabulek jsou v jednotném čísle.</span><span class="sxs-lookup"><span data-stu-id="25e28-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="25e28-216">Když vytváří <xref:System.Data.Linq.DataContext> vlastnosti pro tabulky, názvy tabulek jsou plural.</span><span class="sxs-lookup"><span data-stu-id="25e28-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="25e28-217">Tabulky v ukázkové databázi Northwind jsou shodou okolností již v množném čísle.</span><span class="sxs-lookup"><span data-stu-id="25e28-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="25e28-218">Proto neuvidíte, jak tato část funguje.</span><span class="sxs-lookup"><span data-stu-id="25e28-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="25e28-219">Přestože jsou názvy tabulek databáze zpravidla zapisovány v jednotném čísle, v rozhraní .NET je rovněž obvyklé pojmenovávání kolekcí v množném čísle.</span><span class="sxs-lookup"><span data-stu-id="25e28-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25e28-220">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25e28-220">See also</span></span>

- [<span data-ttu-id="25e28-221">Postupy: Generování objektového modelu v Visual Basic neboC#</span><span class="sxs-lookup"><span data-stu-id="25e28-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="25e28-222">Generování kódu v LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="25e28-222">Code Generation in LINQ to SQL</span></span>](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="25e28-223">Externí mapování</span><span class="sxs-lookup"><span data-stu-id="25e28-223">External Mapping</span></span>](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
