---
title: Mgmtclassgen.exe (spravovaný generátor tříd se silnými typy)
description: Pochopení Mgmtclassgen.exe generátoru třídy pro správu silného typu. Tento nástroj vám umožní rychle vygenerovat spravovanou třídu s časnou vazbou pro třídu WMI.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
ms.openlocfilehash: 89facd4369dad6168e46febd3e34d7f7c235faf0
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517292"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a><span data-ttu-id="14230-104">Mgmtclassgen.exe (spravovaný generátor tříd se silnými typy)</span><span class="sxs-lookup"><span data-stu-id="14230-104">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>
<span data-ttu-id="14230-105">Nástroj Management Strongly Typed Class Generator umožňuje rychle generovat spravovanou třídu s časnou vazbou pro zadanou třídu Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="14230-105">The Management Strongly Typed Class Generator tool enables you to quickly generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span> <span data-ttu-id="14230-106">Vygenerovaná třída usnadňuje psaní kódu pro přístup k instanci třídy WMI.</span><span class="sxs-lookup"><span data-stu-id="14230-106">The generated class simplifies the code you must write to access an instance of the WMI class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14230-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="14230-107">Syntax</span></span>  
  
```console  
mgmtclassgen
WMIClass [options]
```  
  
|<span data-ttu-id="14230-108">Argument</span><span class="sxs-lookup"><span data-stu-id="14230-108">Argument</span></span>|<span data-ttu-id="14230-109">Description</span><span class="sxs-lookup"><span data-stu-id="14230-109">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="14230-110">*WMIClass*</span><span class="sxs-lookup"><span data-stu-id="14230-110">*WMIClass*</span></span>|<span data-ttu-id="14230-111">Třída WMI, pro kterou chcete generovat spravovanou třídu s časnou vazbou.</span><span class="sxs-lookup"><span data-stu-id="14230-111">The Windows Management Instrumentation class for which to generate an early-bound managed class.</span></span>|  
  
|<span data-ttu-id="14230-112">Možnost</span><span class="sxs-lookup"><span data-stu-id="14230-112">Option</span></span>|<span data-ttu-id="14230-113">Popis</span><span class="sxs-lookup"><span data-stu-id="14230-113">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="14230-114">**/l**  *jazyk*</span><span class="sxs-lookup"><span data-stu-id="14230-114">**/l**  *language*</span></span>|<span data-ttu-id="14230-115">Určuje jazyk, ve kterém chcete vygenerovat spravovanou třídu s časnou vazbou.</span><span class="sxs-lookup"><span data-stu-id="14230-115">Specifies the language in which to generate the early-bound managed class.</span></span> <span data-ttu-id="14230-116">Jako argument jazyka můžete zadat **cs** (C#; default), **VB** (Visual Basic), **MC** (C++) nebo **js** (JScript).</span><span class="sxs-lookup"><span data-stu-id="14230-116">You can specify **CS** (C#; default), **VB** (Visual Basic),  **MC** (C++), or **JS** (JScript) as the language argument.</span></span>|  
|<span data-ttu-id="14230-117">**/m**  *počítač*</span><span class="sxs-lookup"><span data-stu-id="14230-117">**/m**  *machine*</span></span>|<span data-ttu-id="14230-118">Určuje počítač, na kterém je uložena třída WMI a ke kterému je třeba se připojit.</span><span class="sxs-lookup"><span data-stu-id="14230-118">Specifies the computer to connect to, where the WMI class resides.</span></span> <span data-ttu-id="14230-119">Výchozí hodnotou je místní počítač.</span><span class="sxs-lookup"><span data-stu-id="14230-119">The default is the local computer.</span></span>|  
|<span data-ttu-id="14230-120">**/n**  *cesta*</span><span class="sxs-lookup"><span data-stu-id="14230-120">**/n**  *path*</span></span>|<span data-ttu-id="14230-121">Určuje cestu k oboru názvů služby WMI, který obsahuje třídu WMI.</span><span class="sxs-lookup"><span data-stu-id="14230-121">Specifies the path to the WMI namespace that contains the WMI class.</span></span> <span data-ttu-id="14230-122">Pokud tuto možnost nezadáte, nástroj vygeneruje kód pro *WMIClass* ve výchozím oboru názvů **root\cimv2** .</span><span class="sxs-lookup"><span data-stu-id="14230-122">If you do not specify this option, the tool generates code for *WMIClass* in the default **Root\cimv2** namespace.</span></span>|  
|<span data-ttu-id="14230-123">**/o**  *classnamespace*</span><span class="sxs-lookup"><span data-stu-id="14230-123">**/o**  *classnamespace*</span></span>|<span data-ttu-id="14230-124">Určuje obor názvů .NET, ve kterém chcete vygenerovat spravovanou třídu kódů.</span><span class="sxs-lookup"><span data-stu-id="14230-124">Specifies the .NET namespace in which to generate the managed code class.</span></span> <span data-ttu-id="14230-125">Pokud tuto možnost nezadáte, nástroj vygeneruje obor názvů pomocí oboru názvů WMI a předpony schématu.</span><span class="sxs-lookup"><span data-stu-id="14230-125">If you do not specify this option, the tool generates the namespace using the WMI namespace and the schema prefix.</span></span> <span data-ttu-id="14230-126">Předpona schématu je část názvu třídy před podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="14230-126">The schema prefix is the part of the class name preceding the underscore character.</span></span> <span data-ttu-id="14230-127">Například pro třídu **Win32_OperatingSystem** v oboru názvů **root\cimv2** nástroj vygeneruje třídu v **kořenovém adresáři. Cimv2. Win32**.</span><span class="sxs-lookup"><span data-stu-id="14230-127">For example, for the **Win32_OperatingSystem** class in the **Root\cimv2** namespace, the tool would generate the class in **ROOT.CIMV2.Win32**.</span></span>|  
|<span data-ttu-id="14230-128">**/p**  *FilePath*</span><span class="sxs-lookup"><span data-stu-id="14230-128">**/p**  *filepath*</span></span>|<span data-ttu-id="14230-129">Určuje cestu k souboru, do kterého chcete uložit vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="14230-129">Specifies the path to the file in which to save the generated code.</span></span> <span data-ttu-id="14230-130">Pokud tuto možnost nezadáte, nástroj vytvoří soubor v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="14230-130">If you do not specify this option, the tool creates the file in the current directory.</span></span> <span data-ttu-id="14230-131">Pojmenovává třídu a soubor, ve kterém třídu generuje, pomocí argumentu *WMIClass* .</span><span class="sxs-lookup"><span data-stu-id="14230-131">It names the class and file in which it generates the class using the *WMIClass* argument.</span></span> <span data-ttu-id="14230-132">Název třídy a souboru jsou stejné jako název *WMIClass.*</span><span class="sxs-lookup"><span data-stu-id="14230-132">The name of the class and the file are the same as the name of the *WMIClass.*</span></span> <span data-ttu-id="14230-133">Pokud *WMIClass* obsahuje znak podtržítka, nástroj použije část názvu třídy za znakem podtržítka.</span><span class="sxs-lookup"><span data-stu-id="14230-133">If *WMIClass* contains an underscore character, the tool uses the part of the class name following the underscore character.</span></span> <span data-ttu-id="14230-134">Například pokud je název *WMIClass* ve formátu **Win32_LogicalDisk**, vygenerovaná třída a soubor se jmenuje "logický disk".</span><span class="sxs-lookup"><span data-stu-id="14230-134">For example, if the *WMIClass* name is in the format **Win32_LogicalDisk**, the generated class and file is named "logicaldisk".</span></span> <span data-ttu-id="14230-135">Pokud soubor již existuje, nástroj přepíše existující soubor.</span><span class="sxs-lookup"><span data-stu-id="14230-135">If a file already exists, the tool overwrites the existing file.</span></span>|  
|<span data-ttu-id="14230-136">**/PW**  *heslo*</span><span class="sxs-lookup"><span data-stu-id="14230-136">**/pw**  *password*</span></span>|<span data-ttu-id="14230-137">Určuje heslo, které se má použít při přihlášení k počítači určenému možností **/m** .</span><span class="sxs-lookup"><span data-stu-id="14230-137">Specifies the password to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="14230-138">**/u**  *uživatelské jméno*</span><span class="sxs-lookup"><span data-stu-id="14230-138">**/u**  *user name*</span></span>|<span data-ttu-id="14230-139">Určuje uživatelské jméno, které se má použít při přihlášení k počítači určenému možností **/m** .</span><span class="sxs-lookup"><span data-stu-id="14230-139">Specifies the user name to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="14230-140">**/?**</span><span class="sxs-lookup"><span data-stu-id="14230-140">**/?**</span></span>|<span data-ttu-id="14230-141">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="14230-141">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14230-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14230-142">Remarks</span></span>  
 <span data-ttu-id="14230-143">Mgmtclassgen.exe používá <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="14230-143">Mgmtclassgen.exe uses the <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="14230-144">Proto můžete použít libovolného zprostředkovatele vlastního kódu k vygenerování kódu v jiných spravovaných jazycích než C#, Visual Basic a JScript.</span><span class="sxs-lookup"><span data-stu-id="14230-144">Therefore, you can use any custom code provider to generate code in managed languages other than C#, Visual Basic, and JScript.</span></span>  
  
 <span data-ttu-id="14230-145">Vygenerované třídy jsou svázány se schématem, pro které byly vygenerovány.</span><span class="sxs-lookup"><span data-stu-id="14230-145">Note that generated classes are bound to the schema for which they are generated.</span></span> <span data-ttu-id="14230-146">Pokud se změní podkladové schéma, musíte znovu vygenerovat třídu, jestliže chcete, aby se změny projevily ve schématu.</span><span class="sxs-lookup"><span data-stu-id="14230-146">If the underlying schema changes, you must regenerate the class if you want it to reflect changes to the schema.</span></span>  
  
 <span data-ttu-id="14230-147">Následující tabulka ukazuje, jak mapovat model WMI Common Information Model (CIM) na datové typy ve vygenerované třídě:</span><span class="sxs-lookup"><span data-stu-id="14230-147">The following table shows how WMI Common Information Model (CIM) types map to data types in a generated class:</span></span>  
  
|<span data-ttu-id="14230-148">Typ CIM</span><span class="sxs-lookup"><span data-stu-id="14230-148">CIM type</span></span>|<span data-ttu-id="14230-149">Datový typ ve vygenerované třídě</span><span class="sxs-lookup"><span data-stu-id="14230-149">Data type in the generated class</span></span>|  
|--------------|--------------------------------------|  
|<span data-ttu-id="14230-150">CIM_SINT8</span><span class="sxs-lookup"><span data-stu-id="14230-150">CIM_SINT8</span></span>|<span data-ttu-id="14230-151">**SByte**</span><span class="sxs-lookup"><span data-stu-id="14230-151">**SByte**</span></span>|  
|<span data-ttu-id="14230-152">CIM_UINT8</span><span class="sxs-lookup"><span data-stu-id="14230-152">CIM_UINT8</span></span>|<span data-ttu-id="14230-153">**Bytové**</span><span class="sxs-lookup"><span data-stu-id="14230-153">**Byte**</span></span>|  
|<span data-ttu-id="14230-154">CIM_SINT16</span><span class="sxs-lookup"><span data-stu-id="14230-154">CIM_SINT16</span></span>|<span data-ttu-id="14230-155">**Int16**</span><span class="sxs-lookup"><span data-stu-id="14230-155">**Int16**</span></span>|  
|<span data-ttu-id="14230-156">CIM_UINT16</span><span class="sxs-lookup"><span data-stu-id="14230-156">CIM_UINT16</span></span>|<span data-ttu-id="14230-157">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="14230-157">**UInt16**</span></span>|  
|<span data-ttu-id="14230-158">CIM_SINT32</span><span class="sxs-lookup"><span data-stu-id="14230-158">CIM_SINT32</span></span>|<span data-ttu-id="14230-159">**Int32**</span><span class="sxs-lookup"><span data-stu-id="14230-159">**Int32**</span></span>|  
|<span data-ttu-id="14230-160">SIM_UINT32</span><span class="sxs-lookup"><span data-stu-id="14230-160">SIM_UINT32</span></span>|<span data-ttu-id="14230-161">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="14230-161">**UInt32**</span></span>|  
|<span data-ttu-id="14230-162">CIM_SINT64</span><span class="sxs-lookup"><span data-stu-id="14230-162">CIM_SINT64</span></span>|<span data-ttu-id="14230-163">**Int64**</span><span class="sxs-lookup"><span data-stu-id="14230-163">**Int64**</span></span>|  
|<span data-ttu-id="14230-164">CIM_UINT64</span><span class="sxs-lookup"><span data-stu-id="14230-164">CIM_UINT64</span></span>|<span data-ttu-id="14230-165">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="14230-165">**UInt64**</span></span>|  
|<span data-ttu-id="14230-166">CIM_REAL32</span><span class="sxs-lookup"><span data-stu-id="14230-166">CIM_REAL32</span></span>|<span data-ttu-id="14230-167">**Jeden**</span><span class="sxs-lookup"><span data-stu-id="14230-167">**Single**</span></span>|  
|<span data-ttu-id="14230-168">CIM_REAL64</span><span class="sxs-lookup"><span data-stu-id="14230-168">CIM_REAL64</span></span>|<span data-ttu-id="14230-169">**dvojité**</span><span class="sxs-lookup"><span data-stu-id="14230-169">**Double**</span></span>|  
|<span data-ttu-id="14230-170">CIM_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="14230-170">CIM_BOOLEAN</span></span>|<span data-ttu-id="14230-171">**Logická hodnota**</span><span class="sxs-lookup"><span data-stu-id="14230-171">**Boolean**</span></span>|  
|<span data-ttu-id="14230-172">CIM_String</span><span class="sxs-lookup"><span data-stu-id="14230-172">CIM_String</span></span>|<span data-ttu-id="14230-173">**Řetězec**</span><span class="sxs-lookup"><span data-stu-id="14230-173">**String**</span></span>|  
|<span data-ttu-id="14230-174">CIM_DATETIME</span><span class="sxs-lookup"><span data-stu-id="14230-174">CIM_DATETIME</span></span>|<span data-ttu-id="14230-175">**Datum a čas** nebo **časový** rozsah</span><span class="sxs-lookup"><span data-stu-id="14230-175">**DateTime** or **TimeSpan**</span></span>|  
|<span data-ttu-id="14230-176">CIM_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="14230-176">CIM_REFERENCE</span></span>|<span data-ttu-id="14230-177">**ManagementPath**</span><span class="sxs-lookup"><span data-stu-id="14230-177">**ManagementPath**</span></span>|  
|<span data-ttu-id="14230-178">CIM_CHAR16</span><span class="sxs-lookup"><span data-stu-id="14230-178">CIM_CHAR16</span></span>|<span data-ttu-id="14230-179">**Char**</span><span class="sxs-lookup"><span data-stu-id="14230-179">**Char**</span></span>|  
|<span data-ttu-id="14230-180">CIM_OBJECT</span><span class="sxs-lookup"><span data-stu-id="14230-180">CIM_OBJECT</span></span>|<span data-ttu-id="14230-181">**ManagementBaseObject**</span><span class="sxs-lookup"><span data-stu-id="14230-181">**ManagementBaseObject**</span></span>|  
|<span data-ttu-id="14230-182">CIM_IUNKNOWN</span><span class="sxs-lookup"><span data-stu-id="14230-182">CIM_IUNKNOWN</span></span>|<span data-ttu-id="14230-183">**Předmětů**</span><span class="sxs-lookup"><span data-stu-id="14230-183">**Object**</span></span>|  
|<span data-ttu-id="14230-184">CIM_ARRAY</span><span class="sxs-lookup"><span data-stu-id="14230-184">CIM_ARRAY</span></span>|<span data-ttu-id="14230-185">Pole objektů uvedených výše</span><span class="sxs-lookup"><span data-stu-id="14230-185">Array of the above mentioned objects</span></span>|  
  
 <span data-ttu-id="14230-186">Při generování třídy WMI si všimněte následujícího chování:</span><span class="sxs-lookup"><span data-stu-id="14230-186">Note the following behaviors when you generate a WMI class:</span></span>  
  
- <span data-ttu-id="14230-187">Standardní veřejná vlastnost nebo metoda může mít stejný název jako existující vlastnost nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="14230-187">It is possible for a standard public property or method to have the same name as an existing property or method.</span></span> <span data-ttu-id="14230-188">V tomto případě nástroj změní název vlastnosti nebo metody ve vygenerované třídě, aby předešel konfliktům názvů.</span><span class="sxs-lookup"><span data-stu-id="14230-188">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="14230-189">Název vlastnosti nebo metody ve vygenerované třídě může být klíčovým slovem v cílovém programovacím jazyku.</span><span class="sxs-lookup"><span data-stu-id="14230-189">It is possible for the name of a property or method in a generated class to be a keyword in the target programming language.</span></span> <span data-ttu-id="14230-190">V tomto případě nástroj změní název vlastnosti nebo metody ve vygenerované třídě, aby předešel konfliktům názvů.</span><span class="sxs-lookup"><span data-stu-id="14230-190">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="14230-191">Kvalifikátory jsou ve službě WMI modifikátory obsahující informace popisující třídu, instanci, vlastnost nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="14230-191">In WMI, qualifiers are modifiers that contain information to describe a class, instance, property, or method.</span></span> <span data-ttu-id="14230-192">Rozhraní WMI používá standardní kvalifikátory, jako je **čtení**, **zápis**a **klíč** , k popisu vlastnosti ve vygenerované třídě.</span><span class="sxs-lookup"><span data-stu-id="14230-192">WMI uses standard qualifiers such as **Read**, **Write**, and **Key** to describe a property in a generated class.</span></span> <span data-ttu-id="14230-193">Například vlastnost, která je upravena s kvalifikátorem **Read** , je definována pouze pomocí přístupového objektu **Get** ve vygenerované třídě.</span><span class="sxs-lookup"><span data-stu-id="14230-193">For example, a property that is modified with a **Read** qualifier is defined only with a property **get** accessor in the generated class.</span></span> <span data-ttu-id="14230-194">Vzhledem k tomu, že vlastnost označená kvalifikátorem **Read** je určena jen pro čtení, není definován přistupující objekt **set** .</span><span class="sxs-lookup"><span data-stu-id="14230-194">Because a property marked with the **Read** qualifier is intended to be read-only, a **set** accessor is not defined.</span></span>  
  
- <span data-ttu-id="14230-195">Číselná vlastnost může být upravena **hodnotami** a kvalifikátory **ValueMaps** k označení toho, že vlastnost může být nastavena pouze na zadané přípustné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="14230-195">A numeric property can be modified by the **Values** and **ValueMaps** qualifiers to indicate that the property can be set only to specified permissible values.</span></span> <span data-ttu-id="14230-196">Výčet se generuje s těmito **hodnotami** a **ValueMaps** a vlastnost je namapována na výčet.</span><span class="sxs-lookup"><span data-stu-id="14230-196">An enumeration is generated with these **Values** and **ValueMaps** and the property is mapped to the enumeration.</span></span>  
  
- <span data-ttu-id="14230-197">Služba WMI používá k popisu třídy, která může mít pouze jednu instanci, pojem singleton.</span><span class="sxs-lookup"><span data-stu-id="14230-197">The WMI uses the term singleton to describe a class that can have only one instance.</span></span> <span data-ttu-id="14230-198">Proto konstruktor bez parametrů pro třídu singleton bude inicializovat třídu pouze do jediné instance třídy.</span><span class="sxs-lookup"><span data-stu-id="14230-198">Therefore, the parameterless constructor for a singleton class will initialize the class to the only instance of the class.</span></span>  
  
- <span data-ttu-id="14230-199">Třída WMI může mít vlastnosti, které jsou objekty.</span><span class="sxs-lookup"><span data-stu-id="14230-199">A WMI class can have properties that are objects.</span></span> <span data-ttu-id="14230-200">Při generování třídy silného typu pro tento typ třídy služby WMI byste měli zvážit generování tříd silného typu pro typy vložených objektů.</span><span class="sxs-lookup"><span data-stu-id="14230-200">When you generate a strongly typed class for this type of WMI class, you should consider generating strongly typed classes for the types of the embedded object properties.</span></span> <span data-ttu-id="14230-201">To vám umožní přístup k vloženým objektům způsobem silného typu.</span><span class="sxs-lookup"><span data-stu-id="14230-201">This will allow you to access the embedded objects in a strongly typed manner.</span></span> <span data-ttu-id="14230-202">Vygenerovaný kód nemusí být schopen rozpoznat typ vloženého objektu.</span><span class="sxs-lookup"><span data-stu-id="14230-202">Note that the generated code might not be able to detect the type of the embedded object.</span></span> <span data-ttu-id="14230-203">V tomto případě bude v generovaném kódu vytvořen komentář, který vás na tento problém upozorní.</span><span class="sxs-lookup"><span data-stu-id="14230-203">In this case, a comment will be created in the generated code to notify you of this issue.</span></span> <span data-ttu-id="14230-204">Pak můžete vygenerovaný kód upravit a zadat vlastnost pro další generovanou třídu.</span><span class="sxs-lookup"><span data-stu-id="14230-204">You can then modify the generated code to type the property to the other generated class.</span></span>  
  
- <span data-ttu-id="14230-205">Ve službě WMI mohou datové hodnoty datového typu CIM_DATETIME představovat konkrétní datum a čas nebo časový interval.</span><span class="sxs-lookup"><span data-stu-id="14230-205">In WMI, the data value of the CIM_DATETIME data type can represent either a specific date and time or a time interval.</span></span> <span data-ttu-id="14230-206">Pokud hodnota dat představuje datum a čas, datový typ ve vygenerované třídě je **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="14230-206">If the data value represents a date and time, the data type in the generated class is **DateTime**.</span></span> <span data-ttu-id="14230-207">Pokud hodnota dat představuje časový interval, datový typ ve vygenerované třídě je **TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="14230-207">If the data value represents a time interval, the data type in the generated class is **TimeSpan**.</span></span>  
  
 <span data-ttu-id="14230-208">Pomocí rozšíření pro správu Průzkumník serveru v sadě Visual Studio .NET můžete alternativně vygenerovat třídu silného typu.</span><span class="sxs-lookup"><span data-stu-id="14230-208">You can alternately generate a strongly typed class using the Server Explorer Management Extension in Visual Studio .NET.</span></span>  
  
 <span data-ttu-id="14230-209">Další informace o rozhraní WMI naleznete v tématu **rozhraní WMI (Windows Management Instrumentation)** v dokumentaci k sadě SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="14230-209">For more information about WMI, see the **Windows Management Instrumentation** topic in the Platform SDK documentation.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="14230-210">Příklady</span><span class="sxs-lookup"><span data-stu-id="14230-210">Examples</span></span>  
 <span data-ttu-id="14230-211">Následující příkaz vygeneruje spravovanou třídu v kódu jazyka C# pro **Win32_LogicalDisk** třídu služby WMI v oboru názvů **root\cimv2** .</span><span class="sxs-lookup"><span data-stu-id="14230-211">The following command generates a managed class in C# code for the **Win32_LogicalDisk** WMI class in the **Root\cimv2** namespace.</span></span> <span data-ttu-id="14230-212">Nástroj zapíše spravovanou třídu do zdrojového souboru na c:\disk.cs v \*\*kořenovém adresáři. Cimv2. \*\*Obor názvů Win32.</span><span class="sxs-lookup"><span data-stu-id="14230-212">The tool writes the managed class to the source file at c:\disk.cs in the **ROOT.CIMV2.Win32** namespace.</span></span>  
  
```console  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 <span data-ttu-id="14230-213">Následující příklad kódu ukazuje, jak používat vygenerovanou třídu při programování.</span><span class="sxs-lookup"><span data-stu-id="14230-213">The following code example shows how to use a generated class programmatically.</span></span> <span data-ttu-id="14230-214">Nejprve se vypočítá instance třídy a vytiskne se cesta.</span><span class="sxs-lookup"><span data-stu-id="14230-214">First, an instance of the class is enumerated and the path is printed.</span></span> <span data-ttu-id="14230-215">Poté se pomocí instance WMI vytvoří instance generované třídy, která má být inicializována.</span><span class="sxs-lookup"><span data-stu-id="14230-215">Next, an instance of the generated class to be initialized is created with an instance of WMI.</span></span> <span data-ttu-id="14230-216">`Process`je třída vygenerovaná pro **Win32_Process** a `LogicalDisk` je třídou generovanou pro **Win32_LogicalDisk** v oboru názvů **root\cimv2** .</span><span class="sxs-lookup"><span data-stu-id="14230-216">`Process` is the class generated for **Win32_Process** and `LogicalDisk` is the class generated for **Win32_LogicalDisk** in the **Root\cimv2** namespace.</span></span>  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App
   Public Shared Sub Main()
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="14230-217">Viz také</span><span class="sxs-lookup"><span data-stu-id="14230-217">See also</span></span>

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [<span data-ttu-id="14230-218">Nástroje</span><span class="sxs-lookup"><span data-stu-id="14230-218">Tools</span></span>](index.md)
- [<span data-ttu-id="14230-219">Výzvy příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="14230-219">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
