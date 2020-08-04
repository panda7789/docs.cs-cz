---
title: SqlMetal.exe (nástroj pro vytváření kódu)
description: Pochopení SqlMetal.exe nástroje pro generování kódu. Použijte nástroj k vygenerování kódu a mapování pro LINQ to SQL komponentu rozhraní .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: 84cad85a7a9fc4b420b57543b7f258607be4ab52
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517045"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="310f0-104">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="310f0-104">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="310f0-105">Nástroj příkazového řádku SqlMetal generuje kód a mapování pro [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] komponentu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="310f0-105">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="310f0-106">Použitím možností uvedených dále v tomto tématu můžete dát nástroji SqlMetal pokyn, aby provedl několik různých úkonů, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="310f0-106">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="310f0-107">Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování z databáze.</span><span class="sxs-lookup"><span data-stu-id="310f0-107">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="310f0-108">Vygenerování přechodného souboru .dbml (database markup language) z databáze za účelem přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="310f0-108">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="310f0-109">Vygenerování zdrojového kódu a atributů mapování nebo souboru mapování ze souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="310f0-109">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="310f0-110">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="310f0-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="310f0-111">Ve výchozím nastavení se soubor nachází v umístění `drive` : \Program Files\Microsoft SDKs\Windows\v `n.nn` \Bin.</span><span class="sxs-lookup"><span data-stu-id="310f0-111">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="310f0-112">Pokud nenainstalujete aplikaci Visual Studio, můžete také získat soubor SQLMetal stažením [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span><span class="sxs-lookup"><span data-stu-id="310f0-112">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="310f0-113">Vývojáři, kteří používají Visual Studio, mohou také použít Návrhář relací objektů k vygenerování tříd entit.</span><span class="sxs-lookup"><span data-stu-id="310f0-113">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="310f0-114">Metoda využívající příkazový řádek je vhodná u velkých databází.</span><span class="sxs-lookup"><span data-stu-id="310f0-114">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="310f0-115">Protože SqlMetal je nástroj příkazového řádku, můžete ho použít v procesu sestavení.</span><span class="sxs-lookup"><span data-stu-id="310f0-115">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="310f0-116">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="310f0-116">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="310f0-117">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md). Na příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="310f0-117">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="310f0-118">Syntax</span><span class="sxs-lookup"><span data-stu-id="310f0-118">Syntax</span></span>  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="310f0-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="310f0-119">Options</span></span>  
 <span data-ttu-id="310f0-120">Chcete-li zobrazit nejaktuálnější seznam možností, zadejte do `sqlmetal /?` příkazového řádku z nainstalovaného umístění.</span><span class="sxs-lookup"><span data-stu-id="310f0-120">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="310f0-121">**Možnosti připojení**</span><span class="sxs-lookup"><span data-stu-id="310f0-121">**Connection Options**</span></span>  
  
|<span data-ttu-id="310f0-122">Možnost</span><span class="sxs-lookup"><span data-stu-id="310f0-122">Option</span></span>|<span data-ttu-id="310f0-123">Popis</span><span class="sxs-lookup"><span data-stu-id="310f0-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="310f0-124">\**/Server:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="310f0-124">**/server:** *\<name>*</span></span>|<span data-ttu-id="310f0-125">Určuje název databázového serveru.</span><span class="sxs-lookup"><span data-stu-id="310f0-125">Specifies database server name.</span></span>|  
|<span data-ttu-id="310f0-126">\**/Database:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="310f0-126">**/database:** *\<name>*</span></span>|<span data-ttu-id="310f0-127">Určuje katalog databází na serveru.</span><span class="sxs-lookup"><span data-stu-id="310f0-127">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="310f0-128">\**/User:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="310f0-128">**/user:** *\<name>*</span></span>|<span data-ttu-id="310f0-129">Určuje ID přihlášeného uživatele. Výchozí hodnota: použijte ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="310f0-129">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="310f0-130">\**/Password:\*\*\*\<password>*</span><span class="sxs-lookup"><span data-stu-id="310f0-130">**/password:** *\<password>*</span></span>|<span data-ttu-id="310f0-131">Určuje heslo pro přihlášení.</span><span class="sxs-lookup"><span data-stu-id="310f0-131">Specifies logon password.</span></span> <span data-ttu-id="310f0-132">Výchozí hodnota: Použít ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="310f0-132">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="310f0-133">\**/Conn:\*\*\*\<connection string>*</span><span class="sxs-lookup"><span data-stu-id="310f0-133">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="310f0-134">Určuje připojovací řetězec databáze.</span><span class="sxs-lookup"><span data-stu-id="310f0-134">Specifies database connection string.</span></span> <span data-ttu-id="310f0-135">Nelze použít s možnostmi **/Server**, **/Database**, **/User**nebo **/Password** .</span><span class="sxs-lookup"><span data-stu-id="310f0-135">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="310f0-136">Nezahrnujte název souboru do připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="310f0-136">Do not include the file name in the connection string.</span></span> <span data-ttu-id="310f0-137">Místo toho přidejte název souboru do příkazového řádku jako vstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="310f0-137">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="310f0-138">Například následující řádek určuje "c:\northwnd.mdf" jako vstupní soubor: **SQLMetal/Code: "c:\Northwind.cs"/Language: CSharp "c:\northwnd.mdf"**.</span><span class="sxs-lookup"><span data-stu-id="310f0-138">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="310f0-139">\**/timeout:\*\*\*\<seconds>*</span><span class="sxs-lookup"><span data-stu-id="310f0-139">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="310f0-140">Určuje hodnotu časového limitu při přístupu SqlMetal k databázi.</span><span class="sxs-lookup"><span data-stu-id="310f0-140">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="310f0-141">Výchozí hodnota: 0 (to znamená žádný časový limit).</span><span class="sxs-lookup"><span data-stu-id="310f0-141">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="310f0-142">**Možnosti extrakce**</span><span class="sxs-lookup"><span data-stu-id="310f0-142">**Extraction options**</span></span>  
  
|<span data-ttu-id="310f0-143">Možnost</span><span class="sxs-lookup"><span data-stu-id="310f0-143">Option</span></span>|<span data-ttu-id="310f0-144">Popis</span><span class="sxs-lookup"><span data-stu-id="310f0-144">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="310f0-145">**/views**</span><span class="sxs-lookup"><span data-stu-id="310f0-145">**/views**</span></span>|<span data-ttu-id="310f0-146">Extrahuje zobrazení databáze.</span><span class="sxs-lookup"><span data-stu-id="310f0-146">Extracts database views.</span></span>|  
|<span data-ttu-id="310f0-147">**/functions**</span><span class="sxs-lookup"><span data-stu-id="310f0-147">**/functions**</span></span>|<span data-ttu-id="310f0-148">Extrahuje funkce databáze.</span><span class="sxs-lookup"><span data-stu-id="310f0-148">Extracts database functions.</span></span>|  
|<span data-ttu-id="310f0-149">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="310f0-149">**/sprocs**</span></span>|<span data-ttu-id="310f0-150">Extrahuje uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="310f0-150">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="310f0-151">**Možnosti výstupu**</span><span class="sxs-lookup"><span data-stu-id="310f0-151">**Output options**</span></span>  
  
|<span data-ttu-id="310f0-152">Možnost</span><span class="sxs-lookup"><span data-stu-id="310f0-152">Option</span></span>|<span data-ttu-id="310f0-153">Popis</span><span class="sxs-lookup"><span data-stu-id="310f0-153">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="310f0-154">**/dbml** *[: soubor]*</span><span class="sxs-lookup"><span data-stu-id="310f0-154">**/dbml** *[:file]*</span></span>|<span data-ttu-id="310f0-155">Odešle výstup jako .dbml.</span><span class="sxs-lookup"><span data-stu-id="310f0-155">Sends output as .dbml.</span></span> <span data-ttu-id="310f0-156">Nelze použít s možností **/map** .</span><span class="sxs-lookup"><span data-stu-id="310f0-156">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="310f0-157">**/Code** *[: soubor]*</span><span class="sxs-lookup"><span data-stu-id="310f0-157">**/code** *[:file]*</span></span>|<span data-ttu-id="310f0-158">Odešle výstup jako zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="310f0-158">Sends output as source code.</span></span> <span data-ttu-id="310f0-159">Nelze použít s možností **/dbml** .</span><span class="sxs-lookup"><span data-stu-id="310f0-159">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="310f0-160">**/map** *[: soubor]*</span><span class="sxs-lookup"><span data-stu-id="310f0-160">**/map** *[:file]*</span></span>|<span data-ttu-id="310f0-161">Generuje soubor mapování XML namísto atributů.</span><span class="sxs-lookup"><span data-stu-id="310f0-161">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="310f0-162">Nelze použít s možností **/dbml** .</span><span class="sxs-lookup"><span data-stu-id="310f0-162">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="310f0-163">**Různé**</span><span class="sxs-lookup"><span data-stu-id="310f0-163">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="310f0-164">Možnost</span><span class="sxs-lookup"><span data-stu-id="310f0-164">Option</span></span>|<span data-ttu-id="310f0-165">Popis</span><span class="sxs-lookup"><span data-stu-id="310f0-165">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="310f0-166">\**/Language:\*\*\*\<language>*</span><span class="sxs-lookup"><span data-stu-id="310f0-166">**/language:** *\<language>*</span></span>|<span data-ttu-id="310f0-167">Určuje jazyk zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="310f0-167">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="310f0-168">Platný *\<language>* : VB, CSharp.</span><span class="sxs-lookup"><span data-stu-id="310f0-168">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="310f0-169">Výchozí hodnota: Odvozeno z přípony názvu souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="310f0-169">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="310f0-170">\**/Namespace:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="310f0-170">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="310f0-171">Určuje obor názvů generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="310f0-171">Specifies namespace of the generated code.</span></span> <span data-ttu-id="310f0-172">Výchozí hodnota: Žádný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="310f0-172">Default value: no namespace.</span></span>|  
|<span data-ttu-id="310f0-173">\**/Context:\*\*\*\<type>*</span><span class="sxs-lookup"><span data-stu-id="310f0-173">**/context:** *\<type>*</span></span>|<span data-ttu-id="310f0-174">Určuje název třídy datového kontextu.</span><span class="sxs-lookup"><span data-stu-id="310f0-174">Specifies name of data context class.</span></span> <span data-ttu-id="310f0-175">Výchozí hodnota: Odvozen od názvu databáze.</span><span class="sxs-lookup"><span data-stu-id="310f0-175">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="310f0-176">\**/entitybase:\*\*\*\<type>*</span><span class="sxs-lookup"><span data-stu-id="310f0-176">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="310f0-177">Určuje základní třídu z tříd entit v generovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="310f0-177">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="310f0-178">Výchozí hodnota: Entity nemají žádnou základní třídu.</span><span class="sxs-lookup"><span data-stu-id="310f0-178">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="310f0-179">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="310f0-179">**/pluralize**</span></span>|<span data-ttu-id="310f0-180">Automaticky převádí názvy tříd a členů do množného nebo jednotného čísla.</span><span class="sxs-lookup"><span data-stu-id="310f0-180">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="310f0-181">Tato možnost je dostupná pouze v anglické verzi (USA).</span><span class="sxs-lookup"><span data-stu-id="310f0-181">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="310f0-182">\**/Serialization:\*\*\*\<option>*</span><span class="sxs-lookup"><span data-stu-id="310f0-182">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="310f0-183">Generuje serializovatelné třídy.</span><span class="sxs-lookup"><span data-stu-id="310f0-183">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="310f0-184">Platný *\<option>* : None, jednosměrný.</span><span class="sxs-lookup"><span data-stu-id="310f0-184">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="310f0-185">Výchozí hodnota: Žádný.</span><span class="sxs-lookup"><span data-stu-id="310f0-185">Default value: None.</span></span><br /><br /> <span data-ttu-id="310f0-186">Další informace naleznete v tématu [serializace](../data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="310f0-186">For more information, see [Serialization](../data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="310f0-187">**Vstupní soubor**</span><span class="sxs-lookup"><span data-stu-id="310f0-187">**Input File**</span></span>  
  
|<span data-ttu-id="310f0-188">Možnost</span><span class="sxs-lookup"><span data-stu-id="310f0-188">Option</span></span>|<span data-ttu-id="310f0-189">Popis</span><span class="sxs-lookup"><span data-stu-id="310f0-189">Description</span></span>|  
|------------|-----------------|  
|**\<input file>**|<span data-ttu-id="310f0-190">Určuje SQL Server Express soubor. mdf, soubor SQL Server Compact 3,5. sdf nebo zprostředkující soubor. dbml.</span><span class="sxs-lookup"><span data-stu-id="310f0-190">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="310f0-191">Poznámky</span><span class="sxs-lookup"><span data-stu-id="310f0-191">Remarks</span></span>  
 <span data-ttu-id="310f0-192">Funkce SqlMetal ve skutečnosti probíhá ve dvou krocích:</span><span class="sxs-lookup"><span data-stu-id="310f0-192">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="310f0-193">Extrahování metadat databáze do souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="310f0-193">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="310f0-194">Generování výstupního souboru s kódem.</span><span class="sxs-lookup"><span data-stu-id="310f0-194">Generating a code output file.</span></span>  
  
     <span data-ttu-id="310f0-195">Pomocí příslušných možností příkazového řádku můžete vydávat Visual Basic nebo zdrojový kód v jazyce C# nebo můžete vytvoření souboru mapování XML.</span><span class="sxs-lookup"><span data-stu-id="310f0-195">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="310f0-196">Chcete-li extrahovat metadata ze souboru .mdf, musíte zadat název souboru .mdf za všemi ostatními možnostmi.</span><span class="sxs-lookup"><span data-stu-id="310f0-196">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="310f0-197">Pokud se nezadá žádný **/Server** , předpokládá se **localhost/SQLEXPRESS** .</span><span class="sxs-lookup"><span data-stu-id="310f0-197">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="310f0-198">Microsoft SQL Server 2005 vyvolá výjimku, pokud je splněna jedna nebo více z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="310f0-198">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="310f0-199">SqlMetal se pokusí extrahovat uloženou proceduru, která volá sama sebe.</span><span class="sxs-lookup"><span data-stu-id="310f0-199">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="310f0-200">Úroveň vnoření uložené procedury, funkce nebo zobrazení je vyšší než 32.</span><span class="sxs-lookup"><span data-stu-id="310f0-200">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="310f0-201">SqlMetal tuto výjimku zachytí a ohlásí ji jako varování.</span><span class="sxs-lookup"><span data-stu-id="310f0-201">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="310f0-202">Chcete-li zadat název vstupního souboru, přidejte název souboru do příkazového řádku jako vstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="310f0-202">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="310f0-203">Zahrnutí názvu souboru do připojovacího řetězce (pomocí možnosti **/Conn** ) není podporováno.</span><span class="sxs-lookup"><span data-stu-id="310f0-203">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="310f0-204">Příklady</span><span class="sxs-lookup"><span data-stu-id="310f0-204">Examples</span></span>  
 <span data-ttu-id="310f0-205">Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL:</span><span class="sxs-lookup"><span data-stu-id="310f0-205">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="310f0-206">**SQLMetal/Server: MyServer/Database: Northwind/dbml: mymeta. dbml**</span><span class="sxs-lookup"><span data-stu-id="310f0-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="310f0-207">Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL ze souboru .mdf pomocí SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="310f0-207">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="310f0-208">**SQLMetal/dbml: mymeta. dbml mydbfile. mdf**</span><span class="sxs-lookup"><span data-stu-id="310f0-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="310f0-209">Vygenerování souboru .dbml obsahujícího extrahovaná metadata SQL z SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="310f0-209">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="310f0-210">**SQLMetal/Server: .\SQLEXPRESS/dbml: mymeta. dbml/Database: Northwind**</span><span class="sxs-lookup"><span data-stu-id="310f0-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="310f0-211">Vygenerování zdrojového kódu ze souboru metadat .dbml:</span><span class="sxs-lookup"><span data-stu-id="310f0-211">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="310f0-212">**SQLMetal/Namespace: NWIND/Code: NWIND. cs/Language: CSharp mymetal. dbml**</span><span class="sxs-lookup"><span data-stu-id="310f0-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="310f0-213">Vygenerování zdrojového kódu přímo z metadat SQL:</span><span class="sxs-lookup"><span data-stu-id="310f0-213">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="310f0-214">**SQLMetal/Server: MyServer/Database: Northwind/Namespace: NWIND/Code: NWIND. cs/Language: CSharp**</span><span class="sxs-lookup"><span data-stu-id="310f0-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="310f0-215">Když použijete možnost **/pluralize** s ukázkovou databází Northwind, pamatujte na následující chování.</span><span class="sxs-lookup"><span data-stu-id="310f0-215">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="310f0-216">Když SqlMetal vytváří názvy řádků pro tabulky, názvy tabulek jsou v jednotném čísle.</span><span class="sxs-lookup"><span data-stu-id="310f0-216">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="310f0-217">Když vytváří <xref:System.Data.Linq.DataContext> vlastnosti pro tabulky, názvy tabulek jsou plural.</span><span class="sxs-lookup"><span data-stu-id="310f0-217">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="310f0-218">Tabulky v ukázkové databázi Northwind jsou shodou okolností již v množném čísle.</span><span class="sxs-lookup"><span data-stu-id="310f0-218">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="310f0-219">Proto neuvidíte, jak tato část funguje.</span><span class="sxs-lookup"><span data-stu-id="310f0-219">Therefore, you do not see that part working.</span></span> <span data-ttu-id="310f0-220">Přestože jsou názvy tabulek databáze zpravidla zapisovány v jednotném čísle, v rozhraní .NET je rovněž obvyklé pojmenovávání kolekcí v množném čísle.</span><span class="sxs-lookup"><span data-stu-id="310f0-220">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="310f0-221">Viz také</span><span class="sxs-lookup"><span data-stu-id="310f0-221">See also</span></span>

- [<span data-ttu-id="310f0-222">Postupy: Generování objektového modelu v jazyce Visual Basic nebo C#</span><span class="sxs-lookup"><span data-stu-id="310f0-222">How to: Generate the Object Model in Visual Basic or C#</span></span>](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="310f0-223">Generování kódu v LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="310f0-223">Code Generation in LINQ to SQL</span></span>](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="310f0-224">Externí mapování</span><span class="sxs-lookup"><span data-stu-id="310f0-224">External Mapping</span></span>](../data/adonet/sql/linq/external-mapping.md)
