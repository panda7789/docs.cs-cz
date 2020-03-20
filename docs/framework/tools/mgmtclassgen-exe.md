---
title: Mgmtclassgen.exe (spravovaný generátor tříd se silnými typy)
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
ms.openlocfilehash: 5e39670fbb40acb999a243ac86683219f3c89e4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180368"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a><span data-ttu-id="5284b-102">Mgmtclassgen.exe (spravovaný generátor tříd se silnými typy)</span><span class="sxs-lookup"><span data-stu-id="5284b-102">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>
<span data-ttu-id="5284b-103">Nástroj Management Strongly Typed Class Generator umožňuje rychle generovat spravovanou třídu s časnou vazbou pro zadanou třídu Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="5284b-103">The Management Strongly Typed Class Generator tool enables you to quickly generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span> <span data-ttu-id="5284b-104">Vygenerovaná třída usnadňuje psaní kódu pro přístup k instanci třídy WMI.</span><span class="sxs-lookup"><span data-stu-id="5284b-104">The generated class simplifies the code you must write to access an instance of the WMI class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5284b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5284b-105">Syntax</span></span>  
  
```console  
mgmtclassgen
WMIClass [options]
```  
  
|<span data-ttu-id="5284b-106">Argument</span><span class="sxs-lookup"><span data-stu-id="5284b-106">Argument</span></span>|<span data-ttu-id="5284b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5284b-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="5284b-108">*Třída WMIClass*</span><span class="sxs-lookup"><span data-stu-id="5284b-108">*WMIClass*</span></span>|<span data-ttu-id="5284b-109">Třída WMI, pro kterou chcete generovat spravovanou třídu s časnou vazbou.</span><span class="sxs-lookup"><span data-stu-id="5284b-109">The Windows Management Instrumentation class for which to generate an early-bound managed class.</span></span>|  
  
|<span data-ttu-id="5284b-110">Možnost</span><span class="sxs-lookup"><span data-stu-id="5284b-110">Option</span></span>|<span data-ttu-id="5284b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="5284b-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5284b-112">**/l**  *jazyk*</span><span class="sxs-lookup"><span data-stu-id="5284b-112">**/l**  *language*</span></span>|<span data-ttu-id="5284b-113">Určuje jazyk, ve kterém chcete vygenerovat spravovanou třídu s časnou vazbou.</span><span class="sxs-lookup"><span data-stu-id="5284b-113">Specifies the language in which to generate the early-bound managed class.</span></span> <span data-ttu-id="5284b-114">Jako argument jazyka můžete zadat **CS** (C#; výchozí), **VB** (Visual Basic), **MC** (C++) nebo **JS** (JScript).</span><span class="sxs-lookup"><span data-stu-id="5284b-114">You can specify **CS** (C#; default), **VB** (Visual Basic),  **MC** (C++), or **JS** (JScript) as the language argument.</span></span>|  
|<span data-ttu-id="5284b-115">**/m**  *stroj*</span><span class="sxs-lookup"><span data-stu-id="5284b-115">**/m**  *machine*</span></span>|<span data-ttu-id="5284b-116">Určuje počítač, na kterém je uložena třída WMI a ke kterému je třeba se připojit.</span><span class="sxs-lookup"><span data-stu-id="5284b-116">Specifies the computer to connect to, where the WMI class resides.</span></span> <span data-ttu-id="5284b-117">Výchozí hodnotou je místní počítač.</span><span class="sxs-lookup"><span data-stu-id="5284b-117">The default is the local computer.</span></span>|  
|<span data-ttu-id="5284b-118">**/n**  *cesta*</span><span class="sxs-lookup"><span data-stu-id="5284b-118">**/n**  *path*</span></span>|<span data-ttu-id="5284b-119">Určuje cestu k oboru názvů služby WMI, který obsahuje třídu WMI.</span><span class="sxs-lookup"><span data-stu-id="5284b-119">Specifies the path to the WMI namespace that contains the WMI class.</span></span> <span data-ttu-id="5284b-120">Pokud tuto možnost nezadáte, nástroj vygeneruje kód pro *třídu WMIClass* ve výchozím oboru názvů **Root\cimv2.**</span><span class="sxs-lookup"><span data-stu-id="5284b-120">If you do not specify this option, the tool generates code for *WMIClass* in the default **Root\cimv2** namespace.</span></span>|  
|<span data-ttu-id="5284b-121">**/o**  *obor názvů tříd*</span><span class="sxs-lookup"><span data-stu-id="5284b-121">**/o**  *classnamespace*</span></span>|<span data-ttu-id="5284b-122">Určuje obor názvů .NET, ve kterém chcete vygenerovat spravovanou třídu kódů.</span><span class="sxs-lookup"><span data-stu-id="5284b-122">Specifies the .NET namespace in which to generate the managed code class.</span></span> <span data-ttu-id="5284b-123">Pokud tuto možnost nezadáte, nástroj vygeneruje obor názvů pomocí oboru názvů WMI a předpony schématu.</span><span class="sxs-lookup"><span data-stu-id="5284b-123">If you do not specify this option, the tool generates the namespace using the WMI namespace and the schema prefix.</span></span> <span data-ttu-id="5284b-124">Předpona schématu je část názvu třídy před podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="5284b-124">The schema prefix is the part of the class name preceding the underscore character.</span></span> <span data-ttu-id="5284b-125">Například pro **třídu Win32_OperatingSystem** v oboru názvů **Root\cimv2** by nástroj vygeneroval třídu v **ROOT. CIMV2. Win32**.</span><span class="sxs-lookup"><span data-stu-id="5284b-125">For example, for the **Win32_OperatingSystem** class in the **Root\cimv2** namespace, the tool would generate the class in **ROOT.CIMV2.Win32**.</span></span>|  
|<span data-ttu-id="5284b-126">**/p**  *cesta k souboru*</span><span class="sxs-lookup"><span data-stu-id="5284b-126">**/p**  *filepath*</span></span>|<span data-ttu-id="5284b-127">Určuje cestu k souboru, do kterého chcete uložit vygenerovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5284b-127">Specifies the path to the file in which to save the generated code.</span></span> <span data-ttu-id="5284b-128">Pokud tuto možnost nezadáte, nástroj vytvoří soubor v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="5284b-128">If you do not specify this option, the tool creates the file in the current directory.</span></span> <span data-ttu-id="5284b-129">Pojmenuje třídu a soubor, ve kterém generuje třídu pomocí argumentu *WMIClass.*</span><span class="sxs-lookup"><span data-stu-id="5284b-129">It names the class and file in which it generates the class using the *WMIClass* argument.</span></span> <span data-ttu-id="5284b-130">Název třídy a souboru jsou stejné jako název *WMIClass.*</span><span class="sxs-lookup"><span data-stu-id="5284b-130">The name of the class and the file are the same as the name of the *WMIClass.*</span></span> <span data-ttu-id="5284b-131">Pokud *wmiclass* obsahuje znak podtržítka, nástroj používá část názvu třídy za znakem podtržítka.</span><span class="sxs-lookup"><span data-stu-id="5284b-131">If *WMIClass* contains an underscore character, the tool uses the part of the class name following the underscore character.</span></span> <span data-ttu-id="5284b-132">Pokud je například název *wmiclass* ve formátu **Win32_LogicalDisk**, vygenerovaná třída a soubor se nazývají "logicaldisk".</span><span class="sxs-lookup"><span data-stu-id="5284b-132">For example, if the *WMIClass* name is in the format **Win32_LogicalDisk**, the generated class and file is named "logicaldisk".</span></span> <span data-ttu-id="5284b-133">Pokud soubor již existuje, nástroj přepíše existující soubor.</span><span class="sxs-lookup"><span data-stu-id="5284b-133">If a file already exists, the tool overwrites the existing file.</span></span>|  
|<span data-ttu-id="5284b-134">**/pw**  *heslo*</span><span class="sxs-lookup"><span data-stu-id="5284b-134">**/pw**  *password*</span></span>|<span data-ttu-id="5284b-135">Určuje heslo, které se má použít při přihlašování k počítači určenému parametrem **/m.**</span><span class="sxs-lookup"><span data-stu-id="5284b-135">Specifies the password to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="5284b-136">**/u**  *uživatelské jméno*</span><span class="sxs-lookup"><span data-stu-id="5284b-136">**/u**  *user name*</span></span>|<span data-ttu-id="5284b-137">Určuje uživatelské jméno, které má být používáno při přihlašování k počítači určenému parametrem **/m.**</span><span class="sxs-lookup"><span data-stu-id="5284b-137">Specifies the user name to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="5284b-138">**/?**</span><span class="sxs-lookup"><span data-stu-id="5284b-138">**/?**</span></span>|<span data-ttu-id="5284b-139">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="5284b-139">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5284b-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5284b-140">Remarks</span></span>  
 <span data-ttu-id="5284b-141">Mgmtclassgen.exe používá <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="5284b-141">Mgmtclassgen.exe uses the <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5284b-142">Proto můžete použít libovolného zprostředkovatele vlastního kódu k vygenerování kódu v jiných spravovaných jazycích než C#, Visual Basic a JScript.</span><span class="sxs-lookup"><span data-stu-id="5284b-142">Therefore, you can use any custom code provider to generate code in managed languages other than C#, Visual Basic, and JScript.</span></span>  
  
 <span data-ttu-id="5284b-143">Vygenerované třídy jsou svázány se schématem, pro které byly vygenerovány.</span><span class="sxs-lookup"><span data-stu-id="5284b-143">Note that generated classes are bound to the schema for which they are generated.</span></span> <span data-ttu-id="5284b-144">Pokud se změní podkladové schéma, musíte znovu vygenerovat třídu, jestliže chcete, aby se změny projevily ve schématu.</span><span class="sxs-lookup"><span data-stu-id="5284b-144">If the underlying schema changes, you must regenerate the class if you want it to reflect changes to the schema.</span></span>  
  
 <span data-ttu-id="5284b-145">Následující tabulka ukazuje, jak mapovat model WMI Common Information Model (CIM) na datové typy ve vygenerované třídě:</span><span class="sxs-lookup"><span data-stu-id="5284b-145">The following table shows how WMI Common Information Model (CIM) types map to data types in a generated class:</span></span>  
  
|<span data-ttu-id="5284b-146">Typ CIM</span><span class="sxs-lookup"><span data-stu-id="5284b-146">CIM type</span></span>|<span data-ttu-id="5284b-147">Datový typ ve vygenerované třídě</span><span class="sxs-lookup"><span data-stu-id="5284b-147">Data type in the generated class</span></span>|  
|--------------|--------------------------------------|  
|<span data-ttu-id="5284b-148">CIM_SINT8</span><span class="sxs-lookup"><span data-stu-id="5284b-148">CIM_SINT8</span></span>|<span data-ttu-id="5284b-149">**Sbyte**</span><span class="sxs-lookup"><span data-stu-id="5284b-149">**SByte**</span></span>|  
|<span data-ttu-id="5284b-150">CIM_UINT8</span><span class="sxs-lookup"><span data-stu-id="5284b-150">CIM_UINT8</span></span>|<span data-ttu-id="5284b-151">**Byte**</span><span class="sxs-lookup"><span data-stu-id="5284b-151">**Byte**</span></span>|  
|<span data-ttu-id="5284b-152">CIM_SINT16</span><span class="sxs-lookup"><span data-stu-id="5284b-152">CIM_SINT16</span></span>|<span data-ttu-id="5284b-153">**Int16**</span><span class="sxs-lookup"><span data-stu-id="5284b-153">**Int16**</span></span>|  
|<span data-ttu-id="5284b-154">CIM_UINT16</span><span class="sxs-lookup"><span data-stu-id="5284b-154">CIM_UINT16</span></span>|<span data-ttu-id="5284b-155">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="5284b-155">**UInt16**</span></span>|  
|<span data-ttu-id="5284b-156">CIM_SINT32</span><span class="sxs-lookup"><span data-stu-id="5284b-156">CIM_SINT32</span></span>|<span data-ttu-id="5284b-157">**Int32**</span><span class="sxs-lookup"><span data-stu-id="5284b-157">**Int32**</span></span>|  
|<span data-ttu-id="5284b-158">SIM_UINT32</span><span class="sxs-lookup"><span data-stu-id="5284b-158">SIM_UINT32</span></span>|<span data-ttu-id="5284b-159">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="5284b-159">**UInt32**</span></span>|  
|<span data-ttu-id="5284b-160">CIM_SINT64</span><span class="sxs-lookup"><span data-stu-id="5284b-160">CIM_SINT64</span></span>|<span data-ttu-id="5284b-161">**Int64**</span><span class="sxs-lookup"><span data-stu-id="5284b-161">**Int64**</span></span>|  
|<span data-ttu-id="5284b-162">CIM_UINT64</span><span class="sxs-lookup"><span data-stu-id="5284b-162">CIM_UINT64</span></span>|<span data-ttu-id="5284b-163">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="5284b-163">**UInt64**</span></span>|  
|<span data-ttu-id="5284b-164">CIM_REAL32</span><span class="sxs-lookup"><span data-stu-id="5284b-164">CIM_REAL32</span></span>|<span data-ttu-id="5284b-165">**Single**</span><span class="sxs-lookup"><span data-stu-id="5284b-165">**Single**</span></span>|  
|<span data-ttu-id="5284b-166">CIM_REAL64</span><span class="sxs-lookup"><span data-stu-id="5284b-166">CIM_REAL64</span></span>|<span data-ttu-id="5284b-167">**Dvojité**</span><span class="sxs-lookup"><span data-stu-id="5284b-167">**Double**</span></span>|  
|<span data-ttu-id="5284b-168">CIM_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="5284b-168">CIM_BOOLEAN</span></span>|<span data-ttu-id="5284b-169">**Logická hodnota**</span><span class="sxs-lookup"><span data-stu-id="5284b-169">**Boolean**</span></span>|  
|<span data-ttu-id="5284b-170">CIM_String</span><span class="sxs-lookup"><span data-stu-id="5284b-170">CIM_String</span></span>|<span data-ttu-id="5284b-171">**Řetězec**</span><span class="sxs-lookup"><span data-stu-id="5284b-171">**String**</span></span>|  
|<span data-ttu-id="5284b-172">CIM_DATETIME</span><span class="sxs-lookup"><span data-stu-id="5284b-172">CIM_DATETIME</span></span>|<span data-ttu-id="5284b-173">**DateTime** nebo **TimeSpan**</span><span class="sxs-lookup"><span data-stu-id="5284b-173">**DateTime** or **TimeSpan**</span></span>|  
|<span data-ttu-id="5284b-174">CIM_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="5284b-174">CIM_REFERENCE</span></span>|<span data-ttu-id="5284b-175">**Cesta pro správu**</span><span class="sxs-lookup"><span data-stu-id="5284b-175">**ManagementPath**</span></span>|  
|<span data-ttu-id="5284b-176">CIM_CHAR16</span><span class="sxs-lookup"><span data-stu-id="5284b-176">CIM_CHAR16</span></span>|<span data-ttu-id="5284b-177">**Char**</span><span class="sxs-lookup"><span data-stu-id="5284b-177">**Char**</span></span>|  
|<span data-ttu-id="5284b-178">CIM_OBJECT</span><span class="sxs-lookup"><span data-stu-id="5284b-178">CIM_OBJECT</span></span>|<span data-ttu-id="5284b-179">**Objekt ManagementBaseObject**</span><span class="sxs-lookup"><span data-stu-id="5284b-179">**ManagementBaseObject**</span></span>|  
|<span data-ttu-id="5284b-180">CIM_IUNKNOWN</span><span class="sxs-lookup"><span data-stu-id="5284b-180">CIM_IUNKNOWN</span></span>|<span data-ttu-id="5284b-181">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="5284b-181">**Object**</span></span>|  
|<span data-ttu-id="5284b-182">CIM_ARRAY</span><span class="sxs-lookup"><span data-stu-id="5284b-182">CIM_ARRAY</span></span>|<span data-ttu-id="5284b-183">Pole objektů uvedených výše</span><span class="sxs-lookup"><span data-stu-id="5284b-183">Array of the above mentioned objects</span></span>|  
  
 <span data-ttu-id="5284b-184">Při generování třídy WMI si všimněte následujícího chování:</span><span class="sxs-lookup"><span data-stu-id="5284b-184">Note the following behaviors when you generate a WMI class:</span></span>  
  
- <span data-ttu-id="5284b-185">Standardní veřejná vlastnost nebo metoda může mít stejný název jako existující vlastnost nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="5284b-185">It is possible for a standard public property or method to have the same name as an existing property or method.</span></span> <span data-ttu-id="5284b-186">V tomto případě nástroj změní název vlastnosti nebo metody ve vygenerované třídě, aby předešel konfliktům názvů.</span><span class="sxs-lookup"><span data-stu-id="5284b-186">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="5284b-187">Název vlastnosti nebo metody ve vygenerované třídě může být klíčovým slovem v cílovém programovacím jazyku.</span><span class="sxs-lookup"><span data-stu-id="5284b-187">It is possible for the name of a property or method in a generated class to be a keyword in the target programming language.</span></span> <span data-ttu-id="5284b-188">V tomto případě nástroj změní název vlastnosti nebo metody ve vygenerované třídě, aby předešel konfliktům názvů.</span><span class="sxs-lookup"><span data-stu-id="5284b-188">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="5284b-189">Kvalifikátory jsou ve službě WMI modifikátory obsahující informace popisující třídu, instanci, vlastnost nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="5284b-189">In WMI, qualifiers are modifiers that contain information to describe a class, instance, property, or method.</span></span> <span data-ttu-id="5284b-190">WMI používá standardní kvalifikátory, jako je **čtení**, **zápis**a **klíč** k popisu vlastnosti ve generované třídě.</span><span class="sxs-lookup"><span data-stu-id="5284b-190">WMI uses standard qualifiers such as **Read**, **Write**, and **Key** to describe a property in a generated class.</span></span> <span data-ttu-id="5284b-191">Například vlastnost, která je změněna s kvalifikátor **čtení** je definována pouze s vlastnost **získat** přístup v generované třídě.</span><span class="sxs-lookup"><span data-stu-id="5284b-191">For example, a property that is modified with a **Read** qualifier is defined only with a property **get** accessor in the generated class.</span></span> <span data-ttu-id="5284b-192">Vzhledem k tomu, že vlastnost označená kvalifikátorem **pro čtení** je určena jen pro čtení, není definován přístupový objekt **set.**</span><span class="sxs-lookup"><span data-stu-id="5284b-192">Because a property marked with the **Read** qualifier is intended to be read-only, a **set** accessor is not defined.</span></span>  
  
- <span data-ttu-id="5284b-193">Číselnou vlastnost lze upravit kvalifikátory **Values** a **ValueMaps,** která označuje, že vlastnost lze nastavit pouze na zadané přípustné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5284b-193">A numeric property can be modified by the **Values** and **ValueMaps** qualifiers to indicate that the property can be set only to specified permissible values.</span></span> <span data-ttu-id="5284b-194">Výčet je generován s těmito **hodnoty** a **ValueMaps** a vlastnost je mapována na výčtu.</span><span class="sxs-lookup"><span data-stu-id="5284b-194">An enumeration is generated with these **Values** and **ValueMaps** and the property is mapped to the enumeration.</span></span>  
  
- <span data-ttu-id="5284b-195">Služba WMI používá k popisu třídy, která může mít pouze jednu instanci, pojem singleton.</span><span class="sxs-lookup"><span data-stu-id="5284b-195">The WMI uses the term singleton to describe a class that can have only one instance.</span></span> <span data-ttu-id="5284b-196">Proto konstruktor bez parametrů pro třídu singleton inicializuje třídu na jedinou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="5284b-196">Therefore, the parameterless constructor for a singleton class will initialize the class to the only instance of the class.</span></span>  
  
- <span data-ttu-id="5284b-197">Třída WMI může mít vlastnosti, které jsou objekty.</span><span class="sxs-lookup"><span data-stu-id="5284b-197">A WMI class can have properties that are objects.</span></span> <span data-ttu-id="5284b-198">Při generování třídy silného typu pro tento typ třídy WMI byste měli zvážit vygenerování třídy silného typu pro typy vlastností vloženého objektu.</span><span class="sxs-lookup"><span data-stu-id="5284b-198">When you generate a strongly-typed class for this type of WMI class, you should consider generating strongly-typed classes for the types of the embedded object properties.</span></span> <span data-ttu-id="5284b-199">To vám umožní přístup k vloženým objektům silně typovaným způsobem.</span><span class="sxs-lookup"><span data-stu-id="5284b-199">This will allow you to access the embedded objects in a strongly-typed manner.</span></span> <span data-ttu-id="5284b-200">Vygenerovaný kód nemusí být schopen rozpoznat typ vloženého objektu.</span><span class="sxs-lookup"><span data-stu-id="5284b-200">Note that the generated code might not be able to detect the type of the embedded object.</span></span> <span data-ttu-id="5284b-201">V tomto případě bude v generovaném kódu vytvořen komentář, který vás na tento problém upozorní.</span><span class="sxs-lookup"><span data-stu-id="5284b-201">In this case, a comment will be created in the generated code to notify you of this issue.</span></span> <span data-ttu-id="5284b-202">Pak můžete vygenerovaný kód upravit a zadat vlastnost pro další generovanou třídu.</span><span class="sxs-lookup"><span data-stu-id="5284b-202">You can then modify the generated code to type the property to the other generated class.</span></span>  
  
- <span data-ttu-id="5284b-203">Ve službě WMI mohou datové hodnoty datového typu CIM_DATETIME představovat konkrétní datum a čas nebo časový interval.</span><span class="sxs-lookup"><span data-stu-id="5284b-203">In WMI, the data value of the CIM_DATETIME data type can represent either a specific date and time or a time interval.</span></span> <span data-ttu-id="5284b-204">Pokud hodnota dat představuje datum a čas, datový typ v generované třídě je **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="5284b-204">If the data value represents a date and time, the data type in the generated class is **DateTime**.</span></span> <span data-ttu-id="5284b-205">Pokud hodnota dat představuje časový interval, datový typ ve generované třídě je **TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="5284b-205">If the data value represents a time interval, the data type in the generated class is **TimeSpan**.</span></span>  
  
 <span data-ttu-id="5284b-206">Případně můžete vygenerovat třídu silného typu pomocí rozšíření Server Explorer Management Extension aplikace Visual Studio .NET.</span><span class="sxs-lookup"><span data-stu-id="5284b-206">You can alternately generate a strongly-typed class using the Server Explorer Management Extension in Visual Studio .NET.</span></span>  
  
 <span data-ttu-id="5284b-207">Další informace o službě WMI naleznete v tématu **WMI V** dokumentaci k sada Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="5284b-207">For more information about WMI, see the **Windows Management Instrumentation** topic in the Platform SDK documentation.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5284b-208">Příklady</span><span class="sxs-lookup"><span data-stu-id="5284b-208">Examples</span></span>  
 <span data-ttu-id="5284b-209">Následující příkaz generuje spravovanou třídu v kódu jazyka C# pro **třídu Win32_LogicalDisk** WMI v oboru názvů **Root\cimv2.**</span><span class="sxs-lookup"><span data-stu-id="5284b-209">The following command generates a managed class in C# code for the **Win32_LogicalDisk** WMI class in the **Root\cimv2** namespace.</span></span> <span data-ttu-id="5284b-210">Nástroj zapíše spravovanou třídu do zdrojového souboru na adrese c:\disk.cs v **ROOT. CIMV2. Obor názvů win32.**</span><span class="sxs-lookup"><span data-stu-id="5284b-210">The tool writes the managed class to the source file at c:\disk.cs in the **ROOT.CIMV2.Win32** namespace.</span></span>  
  
```console  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 <span data-ttu-id="5284b-211">Následující příklad kódu ukazuje, jak používat vygenerovanou třídu při programování.</span><span class="sxs-lookup"><span data-stu-id="5284b-211">The following code example shows how to use a generated class programmatically.</span></span> <span data-ttu-id="5284b-212">Nejprve se vypočítá instance třídy a vytiskne se cesta.</span><span class="sxs-lookup"><span data-stu-id="5284b-212">First, an instance of the class is enumerated and the path is printed.</span></span> <span data-ttu-id="5284b-213">Poté se pomocí instance WMI vytvoří instance generované třídy, která má být inicializována.</span><span class="sxs-lookup"><span data-stu-id="5284b-213">Next, an instance of the generated class to be initialized is created with an instance of WMI.</span></span> <span data-ttu-id="5284b-214">`Process`je třída vygenerovaná pro **Win32_Process** a `LogicalDisk` je třídou generovanou pro **Win32_LogicalDisk** v oboru názvů **Root\cimv2.**</span><span class="sxs-lookup"><span data-stu-id="5284b-214">`Process` is the class generated for **Win32_Process** and `LogicalDisk` is the class generated for **Win32_LogicalDisk** in the **Root\cimv2** namespace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5284b-215">Viz také</span><span class="sxs-lookup"><span data-stu-id="5284b-215">See also</span></span>

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [<span data-ttu-id="5284b-216">Nástroje</span><span class="sxs-lookup"><span data-stu-id="5284b-216">Tools</span></span>](index.md)
- [<span data-ttu-id="5284b-217">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="5284b-217">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
