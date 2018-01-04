---
title: "Nástroje Generátor serializátor XML (Sgen.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 005e78c32d49c8c1b204a3ac9376d943311868fd
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xml-serializer-generator-tool-sgenexe"></a><span data-ttu-id="87d82-102">Nástroje Generátor serializátor XML (Sgen.exe)</span><span class="sxs-lookup"><span data-stu-id="87d82-102">XML Serializer Generator Tool (Sgen.exe)</span></span>
<span data-ttu-id="87d82-103">Vytvoří generátor serializátor XML sestavení serializace XML pro typy v zadané sestavení s cílem zlepšit výkon při spuštění <xref:System.Xml.Serialization.XmlSerializer> při serializuje nebo deserializuje objekty zadaného typů.</span><span class="sxs-lookup"><span data-stu-id="87d82-103">The XML Serializer Generator creates an XML serialization assembly for types in a specified assembly in order to improve the startup performance of a <xref:System.Xml.Serialization.XmlSerializer> when it serializes or deserializes objects of the specified types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87d82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87d82-104">Syntax</span></span>  
  
```  
sgen [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87d82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87d82-105">Parameters</span></span>  
  
|<span data-ttu-id="87d82-106">Možnost</span><span class="sxs-lookup"><span data-stu-id="87d82-106">Option</span></span>|<span data-ttu-id="87d82-107">Popis</span><span class="sxs-lookup"><span data-stu-id="87d82-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="87d82-108">**/a**[**ssembly**]**:***filename*</span><span class="sxs-lookup"><span data-stu-id="87d82-108">**/a**[**ssembly**]**:***filename*</span></span>|<span data-ttu-id="87d82-109">Generuje kód serializace pro všechny typy, které jsou součástí sestavení nebo spustitelný soubor určený podle *filename*.</span><span class="sxs-lookup"><span data-stu-id="87d82-109">Generates serialization code for all the types contained in the assembly or executable specified by *filename*.</span></span> <span data-ttu-id="87d82-110">Lze zadat pouze jeden název souboru.</span><span class="sxs-lookup"><span data-stu-id="87d82-110">Only one file name can be provided.</span></span> <span data-ttu-id="87d82-111">Je-li tento argument se opakuje, se používá poslední název souboru.</span><span class="sxs-lookup"><span data-stu-id="87d82-111">If this argument is repeated, the last file name is used.</span></span>|  
|<span data-ttu-id="87d82-112">**/c [ompiler]:** *možnosti*</span><span class="sxs-lookup"><span data-stu-id="87d82-112">**/c[ompiler]:** *options*</span></span>|<span data-ttu-id="87d82-113">Určuje možnosti, které mají být předána do kompilátor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="87d82-113">Specifies the options to pass to the C# compiler.</span></span> <span data-ttu-id="87d82-114">Všechny možnosti csc.exe jsou podporovány při předání kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="87d82-114">All csc.exe options are supported as they are passed to the compiler.</span></span> <span data-ttu-id="87d82-115">To lze použít k určení, že by měl být podepsáno sestavení a k určení souboru s klíčem.</span><span class="sxs-lookup"><span data-stu-id="87d82-115">This can be used to specify that the assembly should be signed and to specify the key file.</span></span>|  
|<span data-ttu-id="87d82-116">**/d**[**ebug**]</span><span class="sxs-lookup"><span data-stu-id="87d82-116">**/d**[**ebug**]</span></span>|<span data-ttu-id="87d82-117">Generuje obrázek, který lze použít se ladicí program.</span><span class="sxs-lookup"><span data-stu-id="87d82-117">Generates an image that can be used with a debugger.</span></span>|  
|<span data-ttu-id="87d82-118">**/f [orce]**</span><span class="sxs-lookup"><span data-stu-id="87d82-118">**/f[orce]**</span></span>|<span data-ttu-id="87d82-119">Vynutí přepsání existující sestavení se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="87d82-119">Forces the overwriting of an existing assembly of the same name.</span></span> <span data-ttu-id="87d82-120">Výchozí hodnota je **false**.</span><span class="sxs-lookup"><span data-stu-id="87d82-120">The default is **false**.</span></span>|  
|<span data-ttu-id="87d82-121">**/ help nebo /?**</span><span class="sxs-lookup"><span data-stu-id="87d82-121">**/help or /?**</span></span>|<span data-ttu-id="87d82-122">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="87d82-122">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="87d82-123">**/k**[**achovat**]</span><span class="sxs-lookup"><span data-stu-id="87d82-123">**/k**[**eep**]</span></span>|<span data-ttu-id="87d82-124">Potlačí odstranění vytvořených zdrojových souborů a jiné dočasné soubory, poté, co byl zkompilován sestavení serializace.</span><span class="sxs-lookup"><span data-stu-id="87d82-124">Suppresses the deletion of the generated source files and other temporary files after they have been compiled into the serialization assembly.</span></span> <span data-ttu-id="87d82-125">To lze použít k určení, zda tento nástroj je generování kódu serializace pro určitý typ.</span><span class="sxs-lookup"><span data-stu-id="87d82-125">This can be used to determine whether the tool is generating serialization code for a particular type.</span></span>|  
|<span data-ttu-id="87d82-126">**/n**[**ologo**]</span><span class="sxs-lookup"><span data-stu-id="87d82-126">**/n**[**ologo**]</span></span>|<span data-ttu-id="87d82-127">Potlačí zobrazování úvodní nápis společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="87d82-127">Suppresses the display of the Microsoft startup banner.</span></span>|  
|<span data-ttu-id="87d82-128">**/o**[**ut**]**:***cesta*</span><span class="sxs-lookup"><span data-stu-id="87d82-128">**/o**[**ut**]**:***path*</span></span>|<span data-ttu-id="87d82-129">Určuje adresář, do kterého chcete uložit vygenerované sestavení.</span><span class="sxs-lookup"><span data-stu-id="87d82-129">Specifies the directory in which to save the generated assembly.</span></span> <span data-ttu-id="87d82-130">**Poznámka:** název generovaného sestavení se skládá z název vstupní sestavení plus "xmlSerializers.dll".</span><span class="sxs-lookup"><span data-stu-id="87d82-130">**Note:**  The name of the generated assembly is composed of the name of the input assembly plus "xmlSerializers.dll".</span></span>|  
|<span data-ttu-id="87d82-131">**/p**[**roxytypes**]</span><span class="sxs-lookup"><span data-stu-id="87d82-131">**/p**[**roxytypes**]</span></span>|<span data-ttu-id="87d82-132">Generuje kód serializace pouze pro typy XML webové služby proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="87d82-132">Generates serialization code only for the XML Web service proxy types.</span></span>|  
|<span data-ttu-id="87d82-133">**/r**[**rnovat**]**:***assemblyfiles*</span><span class="sxs-lookup"><span data-stu-id="87d82-133">**/r**[**eference**]**:***assemblyfiles*</span></span>|<span data-ttu-id="87d82-134">Určuje sestavení, která je odkazováno dle typy vyžadujících serializace XML.</span><span class="sxs-lookup"><span data-stu-id="87d82-134">Specifies the assemblies that are referenced by the types requiring XML serialization.</span></span> <span data-ttu-id="87d82-135">Je možné zadat více souborů sestavení, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="87d82-135">Accepts multiple assembly files separated by commas.</span></span>|  
|<span data-ttu-id="87d82-136">**/s**[**ilent**]</span><span class="sxs-lookup"><span data-stu-id="87d82-136">**/s**[**ilent**]</span></span>|<span data-ttu-id="87d82-137">Potlačí zobrazování zpráv o úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="87d82-137">Suppresses the display of success messages.</span></span>|  
|<span data-ttu-id="87d82-138">**/t**[**adejte**]**:***typu*</span><span class="sxs-lookup"><span data-stu-id="87d82-138">**/t**[**ype**]**:***type*</span></span>|<span data-ttu-id="87d82-139">Generuje kód serializace pouze u zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="87d82-139">Generates serialization code only for the specified type.</span></span>|  
|<span data-ttu-id="87d82-140">**/v**[**erbose**]</span><span class="sxs-lookup"><span data-stu-id="87d82-140">**/v**[**erbose**]</span></span>|<span data-ttu-id="87d82-141">Zobrazí podrobné informace pro ladění.</span><span class="sxs-lookup"><span data-stu-id="87d82-141">Displays verbose output for debugging.</span></span> <span data-ttu-id="87d82-142">Zobrazí seznam typů z cílového sestavení, které nelze serializovat, s <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="87d82-142">Lists types from the target assembly that cannot be serialized with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|<span data-ttu-id="87d82-143">**/?**</span><span class="sxs-lookup"><span data-stu-id="87d82-143">**/?**</span></span>|<span data-ttu-id="87d82-144">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="87d82-144">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87d82-145">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87d82-145">Remarks</span></span>  
 <span data-ttu-id="87d82-146">Pokud není použit generátor serializátor XML, <xref:System.Xml.Serialization.XmlSerializer> generuje serializace kódu a sestavení serializace pro každý typ při každém spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="87d82-146">When the XML Serializer Generator is not used, a <xref:System.Xml.Serialization.XmlSerializer> generates serialization code and a serialization assembly for each type every time an application is run.</span></span> <span data-ttu-id="87d82-147">Chcete-li zlepšit výkon při spuštění serializace XML, použijte nástroj Sgen.exe ke generování těchto sestavení sestavení předem.</span><span class="sxs-lookup"><span data-stu-id="87d82-147">To improve the performance of XML serialization startup, use the Sgen.exe tool to generate those assemblies the assemblies in advance.</span></span> <span data-ttu-id="87d82-148">Tyto sestavení lze nasadit poté s aplikací.</span><span class="sxs-lookup"><span data-stu-id="87d82-148">These assemblies can then be deployed with the application.</span></span>  
  
 <span data-ttu-id="87d82-149">Generátor serializátor XML můžete také zvýšit výkon klienty, kteří používají ke komunikaci se servery, protože proces serializace nesmí být účtovány výkonu, poté klikněte na tlačítko při prvním načtení typ proxy XML webové služby.</span><span class="sxs-lookup"><span data-stu-id="87d82-149">The XML Serializer Generator can also improve the performance of clients that use XML Web service proxies to communicate with servers because the serialization process will not incur a performance hit when the type is loaded the first time.</span></span>  
  
 <span data-ttu-id="87d82-150">Tyto vygenerované sestavení nelze použít na straně serveru webové služby.</span><span class="sxs-lookup"><span data-stu-id="87d82-150">These generated assemblies cannot be used on the server side of a Web service.</span></span> <span data-ttu-id="87d82-151">Tento nástroj je jen pro scénáře ruční serializace a klienti webové služby.</span><span class="sxs-lookup"><span data-stu-id="87d82-151">This tool is only for Web service clients and manual serialization scenarios.</span></span>  
  
 <span data-ttu-id="87d82-152">Pokud sestavení obsahující typ k serializaci název MyType.dll, pak sestavení přidružené serializace bude pojmenován MyType.XmlSerializers.dll.</span><span class="sxs-lookup"><span data-stu-id="87d82-152">If the assembly containing the type to serialize is named MyType.dll, then the associated serialization assembly will be named MyType.XmlSerializers.dll.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="87d82-153">Příklady</span><span class="sxs-lookup"><span data-stu-id="87d82-153">Examples</span></span>  
 <span data-ttu-id="87d82-154">Následující příkaz vytvoří sestavení s názvem Data.XmlSerializers.dll pro serializaci všechny typy, které jsou obsaženy v sestavení s názvem Data.dll.</span><span class="sxs-lookup"><span data-stu-id="87d82-154">The following command creates an assembly named Data.XmlSerializers.dll for serializing all the types contained in the assembly named Data.dll.</span></span>  
  
```  
sgen Data.dll   
```  
  
 <span data-ttu-id="87d82-155">Data.XmlSerializers.dll sestavení lze odkazovat z kódu, který potřebuje k serializaci a deserializaci typy v Data.dll.</span><span class="sxs-lookup"><span data-stu-id="87d82-155">The Data.XmlSerializers.dll assembly can be referenced from code that needs to serialize and deserialize the types in Data.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d82-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="87d82-156">See Also</span></span>  
 [<span data-ttu-id="87d82-157">Nástroje</span><span class="sxs-lookup"><span data-stu-id="87d82-157">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="87d82-158">Přehled webové služby XML</span><span class="sxs-lookup"><span data-stu-id="87d82-158">XML Web Services Overview</span></span>](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d)  
 [<span data-ttu-id="87d82-159">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="87d82-159">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
