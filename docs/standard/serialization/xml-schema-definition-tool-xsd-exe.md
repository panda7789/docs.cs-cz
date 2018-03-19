---
title: "Nástroje definice schématu XML (Xsd.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0e6407fc8da8695da47165ae0ea2c2c6d863ec23
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2018
---
# <a name="xml-schema-definition-tool-xsdexe"></a><span data-ttu-id="81242-102">Nástroje definice schématu XML (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="81242-102">XML Schema Definition Tool (Xsd.exe)</span></span>
<span data-ttu-id="81242-103">Nástroj pro definici schématu XML (Xsd.exe) generuje schématu XML nebo běžné language runtime třídy z XDR, XML a XSD souborů nebo ze třídy v sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="81242-103">The XML Schema Definition (Xsd.exe) tool generates XML schema or common language runtime classes from XDR, XML, and XSD files, or from classes in a runtime assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81242-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81242-104">Syntax</span></span>  
  
```  
xsd file.xdr [/outputdir:directory][/parameters:file.xml]  
xsd file.xml [/outputdir:directory] [/parameters:file.xml]  
xsd file.xsd {/classes | /dataset} [/element:element]   
             [/enableLinqDataSet] [/language:language]   
                          [/namespace:namespace] [/outputdir:directory] [URI:uri]   
                          [/parameters:file.xml]  
xsd {file.dll | file.exe} [/outputdir:directory] [/type:typename [...]][/parameters:file.xml]  
```  
  
## <a name="argument"></a><span data-ttu-id="81242-105">Argument</span><span class="sxs-lookup"><span data-stu-id="81242-105">Argument</span></span>  
  
|<span data-ttu-id="81242-106">Argument</span><span class="sxs-lookup"><span data-stu-id="81242-106">Argument</span></span>|<span data-ttu-id="81242-107">Popis</span><span class="sxs-lookup"><span data-stu-id="81242-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="81242-108">*file.extension*</span><span class="sxs-lookup"><span data-stu-id="81242-108">*file.extension*</span></span>|<span data-ttu-id="81242-109">Určuje vstupní soubor převést.</span><span class="sxs-lookup"><span data-stu-id="81242-109">Specifies the input file to convert.</span></span> <span data-ttu-id="81242-110">Je nutné zadat extensionas jednu z následujících: .xdr, XML, XSD, .dll nebo .exe.</span><span class="sxs-lookup"><span data-stu-id="81242-110">You must specify the extensionas one of the following: .xdr, .xml, .xsd, .dll, or .exe.</span></span><br /><br /> <span data-ttu-id="81242-111">Pokud zadáte soubor schématu XDR (soubory s příponou .xdr), převede Xsd.exe schéma XDR schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="81242-111">If you specify an XDR schema file (.xdr extension), Xsd.exe converts the XDR schema to an XSD schema.</span></span> <span data-ttu-id="81242-112">Výstupní soubor má stejný název jako schéma XDR, ale s příponou XSD.</span><span class="sxs-lookup"><span data-stu-id="81242-112">The output file has the same name as the XDR schema, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="81242-113">Pokud zadáte soubor XML (soubory s příponou XML), Xsd.exe odvodí schéma z dat v souboru a vytvoří schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="81242-113">If you specify an XML file (.xml extension), Xsd.exe infers a schema from the data in the file and produces an XSD schema.</span></span> <span data-ttu-id="81242-114">Výstupní soubor má stejný název jako soubor XML, ale s příponou XSD.</span><span class="sxs-lookup"><span data-stu-id="81242-114">The output file has the same name as the XML file, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="81242-115">Pokud zadáte soubor schématu XML (soubory s příponou XSD), vygeneruje Xsd.exe zdrojový kód pro objekty modulu runtime, které odpovídají schématu XML.</span><span class="sxs-lookup"><span data-stu-id="81242-115">If you specify an XML schema file (.xsd extension), Xsd.exe generates source code for runtime objects that correspond to the XML schema.</span></span><br /><br /> <span data-ttu-id="81242-116">Pokud zadáte soubor sestavení modulu runtime (s příponou .exe nebo .dll), vygeneruje Xsd.exe schémata pro jeden nebo více typů v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="81242-116">If you specify a runtime assembly file (.exe or .dll extension), Xsd.exe generates schemas for one or more types in that assembly.</span></span> <span data-ttu-id="81242-117">Můžete použít `/type` můžete určit typy, pro které se mají vygenerovat schémata.</span><span class="sxs-lookup"><span data-stu-id="81242-117">You can use the `/type` option to specify the types for which to generate schemas.</span></span> <span data-ttu-id="81242-118">Výstup schémata jsou s názvem schema0.xsd, schema1.xsd a tak dále.</span><span class="sxs-lookup"><span data-stu-id="81242-118">The output schemas are named schema0.xsd, schema1.xsd, and so on.</span></span> <span data-ttu-id="81242-119">XSD.exe vytváří více schémat pouze v případě, že daných typů zadejte obor názvů pomocí `XMLRoot` vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="81242-119">Xsd.exe produces multiple schemas only if the given types specify a namespace using the `XMLRoot` custom attribute.</span></span>|  
  
## <a name="general-options"></a><span data-ttu-id="81242-120">Obecné možnosti</span><span class="sxs-lookup"><span data-stu-id="81242-120">General Options</span></span>  
  
|<span data-ttu-id="81242-121">Možnost</span><span class="sxs-lookup"><span data-stu-id="81242-121">Option</span></span>|<span data-ttu-id="81242-122">Popis</span><span class="sxs-lookup"><span data-stu-id="81242-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="81242-123">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="81242-123">**/h**[**elp**]</span></span>|<span data-ttu-id="81242-124">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="81242-124">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="81242-125">**/o**[**utputdir**]**:***directory*</span><span class="sxs-lookup"><span data-stu-id="81242-125">**/o**[**utputdir**]**:***directory*</span></span>|<span data-ttu-id="81242-126">Určuje výstupní soubory v adresáři.</span><span class="sxs-lookup"><span data-stu-id="81242-126">Specifies the directory for output files.</span></span> <span data-ttu-id="81242-127">Tento argument může být pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="81242-127">This argument can appear only once.</span></span> <span data-ttu-id="81242-128">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="81242-128">The default is the current directory.</span></span>|  
|<span data-ttu-id="81242-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="81242-129">**/?**</span></span>|<span data-ttu-id="81242-130">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="81242-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="81242-131">**/P[arameters]:** *file.xml*</span><span class="sxs-lookup"><span data-stu-id="81242-131">**/P[arameters]:** *file.xml*</span></span>|<span data-ttu-id="81242-132">Možnosti pro různé režimy operace čtení ze souboru zadaného .xml.</span><span class="sxs-lookup"><span data-stu-id="81242-132">Read options for various operation modes from the specified .xml file.</span></span> <span data-ttu-id="81242-133">Je zkratka "/ p:".</span><span class="sxs-lookup"><span data-stu-id="81242-133">The short form is '/p:'.</span></span> <span data-ttu-id="81242-134">Další informace naleznete v následující části poznámky.</span><span class="sxs-lookup"><span data-stu-id="81242-134">For more information, see the following Remarks section.</span></span>|  
  
## <a name="xsd-file-options"></a><span data-ttu-id="81242-135">Možnosti souboru XSD</span><span class="sxs-lookup"><span data-stu-id="81242-135">XSD File Options</span></span>  
 <span data-ttu-id="81242-136">Je třeba zadat pouze jeden z následujících možností pro soubory XSD.</span><span class="sxs-lookup"><span data-stu-id="81242-136">You must specify only one of the following options for .xsd files.</span></span>  
  
|<span data-ttu-id="81242-137">Možnost</span><span class="sxs-lookup"><span data-stu-id="81242-137">Option</span></span>|<span data-ttu-id="81242-138">Popis</span><span class="sxs-lookup"><span data-stu-id="81242-138">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="81242-139">**/c**[**lasses**]</span><span class="sxs-lookup"><span data-stu-id="81242-139">**/c**[**lasses**]</span></span>|<span data-ttu-id="81242-140">Vytvoří třídy, které odpovídají zadaným schématu.</span><span class="sxs-lookup"><span data-stu-id="81242-140">Generates classes that correspond to the specified schema.</span></span> <span data-ttu-id="81242-141">Čtení dat XML do objektu, použijte `System.Xml.Serialization.XmlSerializer.Deserializer` metoda.</span><span class="sxs-lookup"><span data-stu-id="81242-141">To read XML data into the object, use the `System.Xml.Serialization.XmlSerializer.Deserializer` method.</span></span>|  
|<span data-ttu-id="81242-142">**/d**[**ataset**]</span><span class="sxs-lookup"><span data-stu-id="81242-142">**/d**[**ataset**]</span></span>|<span data-ttu-id="81242-143">Vygeneruje třídu odvozenou z <xref:System.Data.DataSet> , který odpovídá zadané schéma.</span><span class="sxs-lookup"><span data-stu-id="81242-143">Generates a class derived from <xref:System.Data.DataSet> that corresponds to the specified schema.</span></span> <span data-ttu-id="81242-144">Čtení dat XML do odvozené třídy, použijte `System.Data.DataSet.ReadXml` metoda.</span><span class="sxs-lookup"><span data-stu-id="81242-144">To read XML data into the derived class, use the `System.Data.DataSet.ReadXml` method.</span></span>|  
  
 <span data-ttu-id="81242-145">Můžete také určit některý z následujících možností pro soubory XSD.</span><span class="sxs-lookup"><span data-stu-id="81242-145">You can also specify any of the following options for .xsd files.</span></span>  
  
|<span data-ttu-id="81242-146">Možnost</span><span class="sxs-lookup"><span data-stu-id="81242-146">Option</span></span>|<span data-ttu-id="81242-147">Popis</span><span class="sxs-lookup"><span data-stu-id="81242-147">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="81242-148">**/e**[**lement**]**:***element*</span><span class="sxs-lookup"><span data-stu-id="81242-148">**/e**[**lement**]**:***element*</span></span>|<span data-ttu-id="81242-149">Určuje element ve schématu pro generování kódu pro.</span><span class="sxs-lookup"><span data-stu-id="81242-149">Specifies the element in the schema to generate code for.</span></span> <span data-ttu-id="81242-150">Ve výchozím nastavení jsou zadány všechny elementy.</span><span class="sxs-lookup"><span data-stu-id="81242-150">By default all elements are typed.</span></span> <span data-ttu-id="81242-151">Tento parametr lze zadat více než jednou.</span><span class="sxs-lookup"><span data-stu-id="81242-151">You can specify this argument more than once.</span></span>|  
|<span data-ttu-id="81242-152">**/enableDataBinding**</span><span class="sxs-lookup"><span data-stu-id="81242-152">**/enableDataBinding**</span></span>|<span data-ttu-id="81242-153">Implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní na všechny typy generovaného povolit datové vazby.</span><span class="sxs-lookup"><span data-stu-id="81242-153">Implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface on all generated types to enable data binding.</span></span> <span data-ttu-id="81242-154">Je zkratka `/edb`.</span><span class="sxs-lookup"><span data-stu-id="81242-154">The short form is `/edb`.</span></span>|  
|<span data-ttu-id="81242-155">**/enableLinqDataSet**</span><span class="sxs-lookup"><span data-stu-id="81242-155">**/enableLinqDataSet**</span></span>|<span data-ttu-id="81242-156">(Krátký tvar: `/eld`.) Určuje, že generované datová sada může být dotázán proti pomocí jazyka LINQ k datové.</span><span class="sxs-lookup"><span data-stu-id="81242-156">(Short form: `/eld`.) Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="81242-157">Tato možnost se používá, pokud je také zadán parametr /dataset.</span><span class="sxs-lookup"><span data-stu-id="81242-157">This option is used when the /dataset option is also specified.</span></span> <span data-ttu-id="81242-158">Další informace najdete v tématu [LINQ na DataSet přehled](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) a [dotazování typové datové sady](../../../docs/framework/data/adonet/querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="81242-158">For more information, see [LINQ to DataSet Overview](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) and [Querying Typed DataSets](../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="81242-159">Obecné informace o používání LINQ najdete v tématu [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span><span class="sxs-lookup"><span data-stu-id="81242-159">For general information about using LINQ, see [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span>|  
|<span data-ttu-id="81242-160">**/f**[**ields**]</span><span class="sxs-lookup"><span data-stu-id="81242-160">**/f**[**ields**]</span></span>|<span data-ttu-id="81242-161">Generuje polí místo vlastností.</span><span class="sxs-lookup"><span data-stu-id="81242-161">Generates fields instead of properties.</span></span> <span data-ttu-id="81242-162">Ve výchozím nastavení jsou generovány vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="81242-162">By default, properties are generated.</span></span>|  
|<span data-ttu-id="81242-163">**/l**[**anguage**]**:***language*</span><span class="sxs-lookup"><span data-stu-id="81242-163">**/l**[**anguage**]**:***language*</span></span>|<span data-ttu-id="81242-164">Určuje programovací jazyk, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="81242-164">Specifies the programming language to use.</span></span> <span data-ttu-id="81242-165">Vybrat z `CS` (C#, který je ve výchozím nastavení), `VB` (Visual Basic), `JS` (JScript), nebo `VJS` (Visual J#).</span><span class="sxs-lookup"><span data-stu-id="81242-165">Choose from `CS` (C#, which is the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="81242-166">Můžete také zadat plně kvalifikovaný název třídy implementující<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="81242-166">You can also specify a fully qualified name for a class implementing <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span></span>|  
|<span data-ttu-id="81242-167">**/n**[**amespace**]**:***namespace*</span><span class="sxs-lookup"><span data-stu-id="81242-167">**/n**[**amespace**]**:***namespace*</span></span>|<span data-ttu-id="81242-168">Určuje runtime obor názvů pro generovaný typy.</span><span class="sxs-lookup"><span data-stu-id="81242-168">Specifies the runtime namespace for the generated types.</span></span> <span data-ttu-id="81242-169">Výchozí obor názvů je `Schemas`.</span><span class="sxs-lookup"><span data-stu-id="81242-169">The default namespace is `Schemas`.</span></span>|  
|<span data-ttu-id="81242-170">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="81242-170">**/nologo**</span></span>|<span data-ttu-id="81242-171">Potlačí hlavičky.</span><span class="sxs-lookup"><span data-stu-id="81242-171">Suppresses the banner.</span></span>|  
|<span data-ttu-id="81242-172">**/ORDER**</span><span class="sxs-lookup"><span data-stu-id="81242-172">**/order**</span></span>|<span data-ttu-id="81242-173">Generuje explicitní pořadí identifikátory pro všechny členy částic.</span><span class="sxs-lookup"><span data-stu-id="81242-173">Generates explicit order identifiers on all particle members.</span></span>|  
|<span data-ttu-id="81242-174">**/o [ut]:** *directoryName*</span><span class="sxs-lookup"><span data-stu-id="81242-174">**/o[ut]:** *directoryName*</span></span>|<span data-ttu-id="81242-175">Určuje výstupní adresář pro soubory v.</span><span class="sxs-lookup"><span data-stu-id="81242-175">Specifies the output directory to place the files in.</span></span> <span data-ttu-id="81242-176">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="81242-176">The default is the current directory.</span></span>|  
|<span data-ttu-id="81242-177">**/u**[**ri**]**:***uri*</span><span class="sxs-lookup"><span data-stu-id="81242-177">**/u**[**ri**]**:***uri*</span></span>|<span data-ttu-id="81242-178">Určuje identifikátor URI pro elementy ve schématu pro generování kódu pro.</span><span class="sxs-lookup"><span data-stu-id="81242-178">Specifies the URI for the elements in the schema to generate code for.</span></span> <span data-ttu-id="81242-179">Tento identifikátor URI, pokud je k dispozici, se vztahuje na všechny prvky určené s `/element` možnost.</span><span class="sxs-lookup"><span data-stu-id="81242-179">This URI, if present, applies to all elements specified with the `/element` option.</span></span>|  
  
## <a name="dll-and-exe-file-options"></a><span data-ttu-id="81242-180">Knihovna DLL a EXE soubor možnosti</span><span class="sxs-lookup"><span data-stu-id="81242-180">DLL and EXE File Options</span></span>  
  
|<span data-ttu-id="81242-181">Možnost</span><span class="sxs-lookup"><span data-stu-id="81242-181">Option</span></span>|<span data-ttu-id="81242-182">Popis</span><span class="sxs-lookup"><span data-stu-id="81242-182">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="81242-183">**/t**[**ype**]**:***typename*</span><span class="sxs-lookup"><span data-stu-id="81242-183">**/t**[**ype**]**:***typename*</span></span>|<span data-ttu-id="81242-184">Určuje název typu vytvořit schéma pro.</span><span class="sxs-lookup"><span data-stu-id="81242-184">Specifies the name of the type to create a schema for.</span></span> <span data-ttu-id="81242-185">Můžete zadat více argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="81242-185">You can specify multiple type arguments.</span></span> <span data-ttu-id="81242-186">Pokud *typename* neurčuje obor názvů, odpovídá Xsd.exe všechny typy v sestavení se zadaným typem.</span><span class="sxs-lookup"><span data-stu-id="81242-186">If *typename* does not specify a namespace, Xsd.exe matches all types in the assembly with the specified type.</span></span> <span data-ttu-id="81242-187">Pokud *typename* Určuje obor názvů, pouze je nalezena shoda typu.</span><span class="sxs-lookup"><span data-stu-id="81242-187">If *typename* specifies a namespace, only that type is matched.</span></span> <span data-ttu-id="81242-188">Pokud *typename* končí znak hvězdičky (\*), nástroj odpovídá všechny typy, které začínají řetězcem předchozí \*.</span><span class="sxs-lookup"><span data-stu-id="81242-188">If *typename* ends with an asterisk character (\*), the tool matches all types that start with the string preceding the \*.</span></span> <span data-ttu-id="81242-189">V případě vynechání `/type` možnost, Xsd.exe generuje schémata pro všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="81242-189">If you omit the `/type` option, Xsd.exe generates schemas for all types in the assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81242-190">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81242-190">Remarks</span></span>  
 <span data-ttu-id="81242-191">V následující tabulce jsou uvedeny operace, že provede Xsd.exe.</span><span class="sxs-lookup"><span data-stu-id="81242-191">The following table shows the operations that Xsd.exe performs.</span></span>  
  
 <span data-ttu-id="81242-192">XDR k XSD</span><span class="sxs-lookup"><span data-stu-id="81242-192">XDR to XSD</span></span>  
 <span data-ttu-id="81242-193">Generuje schématu XML ze souboru XML sníženým Data schématu.</span><span class="sxs-lookup"><span data-stu-id="81242-193">Generates an XML schema from an XML-Data-Reduced schema file.</span></span> <span data-ttu-id="81242-194">XDR je ve formátu early založený na jazyce XML schématu.</span><span class="sxs-lookup"><span data-stu-id="81242-194">XDR is an early XML-based schema format.</span></span>  
  
 <span data-ttu-id="81242-195">XML na XSD</span><span class="sxs-lookup"><span data-stu-id="81242-195">XML to XSD</span></span>  
 <span data-ttu-id="81242-196">Generuje schématu XML ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="81242-196">Generates an XML schema from an XML file.</span></span>  
  
 <span data-ttu-id="81242-197">XSD sadu dat</span><span class="sxs-lookup"><span data-stu-id="81242-197">XSD to DataSet</span></span>  
 <span data-ttu-id="81242-198">Generuje modul common language runtime <xref:System.Data.DataSet> třídy ze souboru schématu XSD.</span><span class="sxs-lookup"><span data-stu-id="81242-198">Generates common language runtime <xref:System.Data.DataSet> classes from an XSD schema file.</span></span> <span data-ttu-id="81242-199">Generované třídy poskytují bohatý objektový model pro běžné data XML.</span><span class="sxs-lookup"><span data-stu-id="81242-199">The generated classes provide a rich object model for regular XML data.</span></span>  
  
 <span data-ttu-id="81242-200">XSD do tříd</span><span class="sxs-lookup"><span data-stu-id="81242-200">XSD to Classes</span></span>  
 <span data-ttu-id="81242-201">Generuje runtime třídy ze souboru schématu XSD.</span><span class="sxs-lookup"><span data-stu-id="81242-201">Generates runtime classes from an XSD schema file.</span></span> <span data-ttu-id="81242-202">Generované třídy lze použít ve spojení s <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> ke čtení a zápisu kód XML, který následuje schéma.</span><span class="sxs-lookup"><span data-stu-id="81242-202">The generated classes can be used in conjunction with <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> to read and write XML code that follows the schema.</span></span>  
  
 <span data-ttu-id="81242-203">Třídy, které mají XSD</span><span class="sxs-lookup"><span data-stu-id="81242-203">Classes to XSD</span></span>  
 <span data-ttu-id="81242-204">Generuje schématu XML z typ nebo typy v sestavení soubor za běhu.</span><span class="sxs-lookup"><span data-stu-id="81242-204">Generates an XML schema from a type or types in a runtime assembly file.</span></span> <span data-ttu-id="81242-205">Generované schéma definuje ve formátu XML, který je používán `System.Xml.Serialization.XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="81242-205">The generated schema defines the XML format used by `System.Xml.Serialization.XmlSerializer`.</span></span>  
  
 <span data-ttu-id="81242-206">XSD.exe umožňuje pracovat s schémat XML, které následují definici schématu XML (XSD) jazyk navrhovaná World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="81242-206">Xsd.exe only allows you to manipulate XML schemas that follow the XML Schema Definition (XSD) language proposed by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="81242-207">Další informace o návrhu definice schématu XML nebo formátu XML, najdete v části http://w3.org.</span><span class="sxs-lookup"><span data-stu-id="81242-207">For more information on the XML Schema Definition proposal or the XML standard, see http://w3.org.</span></span>  
  
## <a name="setting-options-with-an-xml-file"></a><span data-ttu-id="81242-208">Nastavení možností pomocí souboru XML</span><span class="sxs-lookup"><span data-stu-id="81242-208">Setting Options with an XML File</span></span>  
 <span data-ttu-id="81242-209">Pomocí `/parameters` přepínače, můžete zadat jeden soubor XML, který nastaví různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="81242-209">By using the `/parameters` switch, you can specify a single XML file that sets various options.</span></span> <span data-ttu-id="81242-210">Možnosti můžete nastavit, závisí na tom, jak používáte nástroj XSD.exe.</span><span class="sxs-lookup"><span data-stu-id="81242-210">The options you can set depend on how you are using the XSD.exe tool.</span></span> <span data-ttu-id="81242-211">Vybrat možnost generování schémat, generování kódu soubory nebo soubory s kódem, mezi které patří generování `DataSet` funkce.</span><span class="sxs-lookup"><span data-stu-id="81242-211">Choices include generating schemas, generating code files, or generating code files that include `DataSet` features.</span></span> <span data-ttu-id="81242-212">Můžete například nastavit `<assembly\>` element na název spustitelného souboru (.exe) nebo souboru typu knihovna (DLL) při generování schématu, ale ne v případě, že generování souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="81242-212">For example, you can set the `<assembly\>` element to the name of an executable (.exe) or type library (.dll) file when generating a schema, but not when generating a code file.</span></span> <span data-ttu-id="81242-213">Následující kód XML ukazuje, jak lze použít `<generateSchemas\>` element se zadaným spustitelného souboru:</span><span class="sxs-lookup"><span data-stu-id="81242-213">The following XML shows how to use the `<generateSchemas\>` element with a specified executable:</span></span>  
  
```xml  
<!-- This is in a file named GenerateSchemas.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <assembly>ConsoleApplication1.exe</assembly>  
</generateSchemas>  
</xsd>  
```  
  
 <span data-ttu-id="81242-214">Pokud předchozí XML je obsažena v souboru s názvem GenerateSchemas.xml, použijte `/parameters` přepínat zadáním následujícího příkazu na příkazovém řádku a stisknutím klávesy ENTER:</span><span class="sxs-lookup"><span data-stu-id="81242-214">If the preceding XML is contained in a file named GenerateSchemas.xml, then use the `/parameters` switch by typing the following at a command prompt and pressing ENTER:</span></span>  
  
 `xsd /p:GenerateSchemas.xml`  
  
 <span data-ttu-id="81242-215">Na druhé straně Pokud jsou generování schéma pro jeden typ nalezen v sestavení, můžete použít následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="81242-215">On the other hand, if you are generating a schema for a single type found in the assembly, you can use the following XML:</span></span>  
  
```xml  
<!-- This is in a file named GenerateSchemaFromType.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <type>IDItems</type>  
</generateSchemas>  
</xsd>  
```  
  
 <span data-ttu-id="81242-216">Ale při použití předcházející kódu, je třeba zadat také název sestavení na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="81242-216">But to use preceding code, you must also supply the name of the assembly at the command prompt.</span></span> <span data-ttu-id="81242-217">Na příkazovém řádku (za předpokladu, že je soubor XML nazvaný GenerateSchemaFromType.xml) zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="81242-217">Type the following at a command prompt (presuming the XML file is named GenerateSchemaFromType.xml):</span></span>  
  
 `xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe`  
  
 <span data-ttu-id="81242-218">Je třeba zadat pouze jeden z následujících možností `\<generateSchemas>` elementu.</span><span class="sxs-lookup"><span data-stu-id="81242-218">You must specify only one of the following options for the `\<generateSchemas>` element.</span></span>  
  
|<span data-ttu-id="81242-219">Prvek</span><span class="sxs-lookup"><span data-stu-id="81242-219">Element</span></span>|<span data-ttu-id="81242-220">Popis</span><span class="sxs-lookup"><span data-stu-id="81242-220">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81242-221">\<sestavení ></span><span class="sxs-lookup"><span data-stu-id="81242-221">\<assembly></span></span>|<span data-ttu-id="81242-222">Určuje sestavení, které chcete vytvořit schéma z.</span><span class="sxs-lookup"><span data-stu-id="81242-222">Specifies an assembly to generate the schema from.</span></span>|  
|<span data-ttu-id="81242-223">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="81242-223">\<type></span></span>|<span data-ttu-id="81242-224">Určuje typ v sestavení, které chcete vytvořit schéma pro nalezen.</span><span class="sxs-lookup"><span data-stu-id="81242-224">Specifies a type found in an assembly to generate a schema for.</span></span>|  
|<span data-ttu-id="81242-225">\<xml></span><span class="sxs-lookup"><span data-stu-id="81242-225">\<xml></span></span>|<span data-ttu-id="81242-226">Určuje soubor XML pro schéma pro generování.</span><span class="sxs-lookup"><span data-stu-id="81242-226">Specifies an XML file to generate a schema for.</span></span>|  
|<span data-ttu-id="81242-227">\<xdr></span><span class="sxs-lookup"><span data-stu-id="81242-227">\<xdr></span></span>|<span data-ttu-id="81242-228">Určuje soubor XDR ke generování schéma pro.</span><span class="sxs-lookup"><span data-stu-id="81242-228">Specifies an XDR file to generate a schema for.</span></span>|  
  
 <span data-ttu-id="81242-229">Chcete-li generovat soubor s kódem, použijte `<generateClasses\>` elementu.</span><span class="sxs-lookup"><span data-stu-id="81242-229">To generate a code file, use the `<generateClasses\>` element.</span></span> <span data-ttu-id="81242-230">Následující příklad generuje soubor kódu.</span><span class="sxs-lookup"><span data-stu-id="81242-230">The following example generates a code file.</span></span> <span data-ttu-id="81242-231">Všimněte si, že jsou také zobrazeny dva atributy, které umožňují nastavit programovací jazyk a obor názvů generovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="81242-231">Note that two attributes are also shown that allow you to set the programming language and namespace of the generated file.</span></span>  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>  
</xsd>  
<!-- You must supply an .xsd file when typing in the command line.-->  
<!-- For example: xsd /p:genClasses mySchema.xsd -->  
```  
  
 <span data-ttu-id="81242-232">Možnosti pro můžete nastavit `\<generateClasses>` element patří následující.</span><span class="sxs-lookup"><span data-stu-id="81242-232">Options you can set for the `\<generateClasses>` element include the following.</span></span>  
  
|<span data-ttu-id="81242-233">Prvek</span><span class="sxs-lookup"><span data-stu-id="81242-233">Element</span></span>|<span data-ttu-id="81242-234">Popis</span><span class="sxs-lookup"><span data-stu-id="81242-234">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81242-235">\<element></span><span class="sxs-lookup"><span data-stu-id="81242-235">\<element></span></span>|<span data-ttu-id="81242-236">Určuje element v souboru XSD pro generování kódu pro.</span><span class="sxs-lookup"><span data-stu-id="81242-236">Specifies an element in the .xsd file to generate code for.</span></span>|  
|<span data-ttu-id="81242-237">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="81242-237">\<schemaImporterExtensions></span></span>|<span data-ttu-id="81242-238">Určuje typu odvozeného z <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="81242-238">Specifies a type derived from the <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> class.</span></span>|  
|<span data-ttu-id="81242-239">\<schema></span><span class="sxs-lookup"><span data-stu-id="81242-239">\<schema></span></span>|<span data-ttu-id="81242-240">Určuje soubor schématu XML pro generování kódu pro.</span><span class="sxs-lookup"><span data-stu-id="81242-240">Specifies a XML Schema file to generate code for.</span></span>  <span data-ttu-id="81242-241">Více souborů schématu XML je možné zadat pomocí několika \<schématu > elementy.</span><span class="sxs-lookup"><span data-stu-id="81242-241">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|  
  
 <span data-ttu-id="81242-242">V následující tabulce jsou uvedeny atributy, které lze také použít s `<generateClasses\>` elementu.</span><span class="sxs-lookup"><span data-stu-id="81242-242">The following table shows the attributes that can also be used with the `<generateClasses\>` element.</span></span>  
  
|<span data-ttu-id="81242-243">Atribut</span><span class="sxs-lookup"><span data-stu-id="81242-243">Attribute</span></span>|<span data-ttu-id="81242-244">Popis</span><span class="sxs-lookup"><span data-stu-id="81242-244">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81242-245">jazyk</span><span class="sxs-lookup"><span data-stu-id="81242-245">language</span></span>|<span data-ttu-id="81242-246">Určuje programovací jazyk, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="81242-246">Specifies the programming language to use.</span></span> <span data-ttu-id="81242-247">Vybrat z `CS` (C#, výchozí nastavení), `VB` (Visual Basic), `JS` (JScript), nebo `VJS` (Visual J#).</span><span class="sxs-lookup"><span data-stu-id="81242-247">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="81242-248">Můžete také zadat plně kvalifikovaný název pro třídu, která implementuje <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="81242-248">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|  
|<span data-ttu-id="81242-249">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="81242-249">namespace</span></span>|<span data-ttu-id="81242-250">Určuje obor názvů pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="81242-250">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="81242-251">Obor názvů musí odpovídat CLR standardů (například bez mezer nebo zpětné lomítko znaků).</span><span class="sxs-lookup"><span data-stu-id="81242-251">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|  
|<span data-ttu-id="81242-252">možnosti</span><span class="sxs-lookup"><span data-stu-id="81242-252">options</span></span>|<span data-ttu-id="81242-253">Jeden z následujících hodnot: `none`, `properties` (vygeneruje vlastnosti místo veřejná pole), `order`, nebo `enableDataBinding` (najdete v článku `/order` a `/enableDataBinding` přepínače v předchozí části Možnosti soubor XSD.</span><span class="sxs-lookup"><span data-stu-id="81242-253">One of the following values: `none`, `properties` (generates properties instead of public fields), `order`, or `enableDataBinding` (see the `/order` and `/enableDataBinding` switches in the preceding XSD File Options section.</span></span>|  
  
 <span data-ttu-id="81242-254">Můžete také určit, jak `DataSet` kód je generována pomocí `<generateDataSets\>` elementu.</span><span class="sxs-lookup"><span data-stu-id="81242-254">You can also control how `DataSet` code is generated by using the `<generateDataSets\>` element.</span></span> <span data-ttu-id="81242-255">Následující kód XML určuje, že generovaný codeuses `DataSet` struktury (například <xref:System.Data.DataTable> – třída) k vytvoření kód jazyka Visual Basic pro zadaný element.</span><span class="sxs-lookup"><span data-stu-id="81242-255">The following XML specifies that the generated codeuses `DataSet` structures (such as the <xref:System.Data.DataTable> class) to create Visual Basic code for a specified element.</span></span> <span data-ttu-id="81242-256">Vygenerovaný struktury datová sada bude podporovat LINQ dotazů.</span><span class="sxs-lookup"><span data-stu-id="81242-256">The generated DataSet structures will support LINQ queries.</span></span>  
  
 `<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>`  
  
 `<generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>`  
  
 `</generateDataSet>`  
  
 `</xsd>`  
  
 <span data-ttu-id="81242-257">Možnosti pro můžete nastavit `<generateDataSet\>` element patří následující.</span><span class="sxs-lookup"><span data-stu-id="81242-257">Options you can set for the `<generateDataSet\>` element include the following.</span></span>  
  
|<span data-ttu-id="81242-258">Prvek</span><span class="sxs-lookup"><span data-stu-id="81242-258">Element</span></span>|<span data-ttu-id="81242-259">Popis</span><span class="sxs-lookup"><span data-stu-id="81242-259">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81242-260">\<schema></span><span class="sxs-lookup"><span data-stu-id="81242-260">\<schema></span></span>|<span data-ttu-id="81242-261">Určuje soubor schématu XML pro generování kódu pro.</span><span class="sxs-lookup"><span data-stu-id="81242-261">Specifies an XML Schema file to generate code for.</span></span> <span data-ttu-id="81242-262">Více souborů schématu XML je možné zadat pomocí několika \<schématu > elementy.</span><span class="sxs-lookup"><span data-stu-id="81242-262">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|  
  
 <span data-ttu-id="81242-263">V následující tabulce jsou uvedeny atributy, které lze používat s `<generateDataSet\>` elementu.</span><span class="sxs-lookup"><span data-stu-id="81242-263">The following table shows the attributes that can be used with the `<generateDataSet\>` element.</span></span>  
  
|<span data-ttu-id="81242-264">Atribut</span><span class="sxs-lookup"><span data-stu-id="81242-264">Attribute</span></span>|<span data-ttu-id="81242-265">Popis</span><span class="sxs-lookup"><span data-stu-id="81242-265">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81242-266">enableLinqDataSet</span><span class="sxs-lookup"><span data-stu-id="81242-266">enableLinqDataSet</span></span>|<span data-ttu-id="81242-267">Určuje, že generované datová sada může být dotázán proti pomocí jazyka LINQ k datové.</span><span class="sxs-lookup"><span data-stu-id="81242-267">Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="81242-268">Výchozí hodnota je False.</span><span class="sxs-lookup"><span data-stu-id="81242-268">The default value is false.</span></span>|  
|<span data-ttu-id="81242-269">jazyk</span><span class="sxs-lookup"><span data-stu-id="81242-269">language</span></span>|<span data-ttu-id="81242-270">Určuje programovací jazyk, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="81242-270">Specifies the programming language to use.</span></span> <span data-ttu-id="81242-271">Vybrat z `CS` (C#, výchozí nastavení), `VB` (Visual Basic), `JS` (JScript), nebo `VJS` (Visual J#).</span><span class="sxs-lookup"><span data-stu-id="81242-271">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="81242-272">Můžete také zadat plně kvalifikovaný název pro třídu, která implementuje <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="81242-272">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|  
|<span data-ttu-id="81242-273">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="81242-273">namespace</span></span>|<span data-ttu-id="81242-274">Určuje obor názvů pro generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="81242-274">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="81242-275">Obor názvů musí odpovídat CLR standardů (například bez mezer nebo zpětné lomítko znaků).</span><span class="sxs-lookup"><span data-stu-id="81242-275">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|  
  
 <span data-ttu-id="81242-276">Atributy, které lze nastavit na nejvyšší úrovni `<xsd\>` elementu.</span><span class="sxs-lookup"><span data-stu-id="81242-276">There are attributes that you can set on the top level `<xsd\>` element.</span></span> <span data-ttu-id="81242-277">Tyto možnosti lze používat s některou z podřízených prvků (`<generateSchemas\>`, `<generateClasses\>` nebo `<generateDataSet\>`).</span><span class="sxs-lookup"><span data-stu-id="81242-277">These options can be used with any of the child elements (`<generateSchemas\>`, `<generateClasses\>` or `<generateDataSet\>`).</span></span> <span data-ttu-id="81242-278">Následující kód XML generuje kód pro element s názvem "IDItems" v adresáři výstupu s názvem "MyOutputDirectory".</span><span class="sxs-lookup"><span data-stu-id="81242-278">The following XML code generates code for an element named "IDItems" in the output directory named "MyOutputDirectory".</span></span>  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>  
<generateClasses>  
<element>IDItems</element>  
</generateClasses>  
</xsd>  
```  
  
 <span data-ttu-id="81242-279">V následující tabulce jsou uvedeny atributy, které lze také použít s `\<xsd>` elementu.</span><span class="sxs-lookup"><span data-stu-id="81242-279">The following table shows the attributes that can also be used with the `\<xsd>` element.</span></span>  
  
|<span data-ttu-id="81242-280">Atribut</span><span class="sxs-lookup"><span data-stu-id="81242-280">Attribute</span></span>|<span data-ttu-id="81242-281">Popis</span><span class="sxs-lookup"><span data-stu-id="81242-281">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81242-282">výstup</span><span class="sxs-lookup"><span data-stu-id="81242-282">output</span></span>|<span data-ttu-id="81242-283">Název adresáře, kde budou umístěny vygenerovaný soubor schématu nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="81242-283">The name of a directory where the generated schema or code file will be placed.</span></span>|  
|<span data-ttu-id="81242-284">nologo</span><span class="sxs-lookup"><span data-stu-id="81242-284">nologo</span></span>|<span data-ttu-id="81242-285">Potlačí hlavičky.</span><span class="sxs-lookup"><span data-stu-id="81242-285">Suppresses the banner.</span></span> <span data-ttu-id="81242-286">Nastavte na `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="81242-286">Set to `true` or `false`.</span></span>|  
|<span data-ttu-id="81242-287">Nápověda</span><span class="sxs-lookup"><span data-stu-id="81242-287">help</span></span>|<span data-ttu-id="81242-288">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="81242-288">Displays command syntax and options for the tool.</span></span> <span data-ttu-id="81242-289">Nastavte na `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="81242-289">Set to `true` or `false`.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="81242-290">Příklady</span><span class="sxs-lookup"><span data-stu-id="81242-290">Examples</span></span>  
 <span data-ttu-id="81242-291">Následující příkaz generuje schématu XML z `myFile.xdr` a uloží jej do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="81242-291">The following command generates an XML schema from `myFile.xdr` and saves it to the current directory.</span></span>  
  
```  
xsd myFile.xdr   
```  
  
 <span data-ttu-id="81242-292">Následující příkaz generuje schématu XML z `myFile.xml` a uloží jej do zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="81242-292">The following command generates an XML schema from `myFile.xml` and saves it to the specified directory.</span></span>  
  
```  
xsd myFile.xml /outputdir:myOutputDir  
```  
  
 <span data-ttu-id="81242-293">Následující příkaz generuje sadu dat, která odpovídá určenému schématu v jazyce C# a uloží jej jako `XSDSchemaFile.cs` v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="81242-293">The following command generates a data set that corresponds to the specified schema in the C# language and saves it as `XSDSchemaFile.cs` in the current directory.</span></span>  
  
```  
xsd /dataset /language:CS XSDSchemaFile.xsd  
```  
  
 <span data-ttu-id="81242-294">Následující příkaz generuje schémat XML pro všechny typy v sestavení `myAssembly.dll` a ukládá je jako `schema0.xsd` v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="81242-294">The following command generates XML schemas for all types in the assembly `myAssembly.dll` and saves them as `schema0.xsd` in the current directory.</span></span>  
  
```  
xsd myAssembly.dll    
```  
  
## <a name="see-also"></a><span data-ttu-id="81242-295">Viz také</span><span class="sxs-lookup"><span data-stu-id="81242-295">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>  
 <span data-ttu-id="81242-296">[Nástroje](../../../docs/framework/tools/index.md)    </span><span class="sxs-lookup"><span data-stu-id="81242-296">[Tools](../../../docs/framework/tools/index.md)    </span></span>  
 [<span data-ttu-id="81242-297">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="81242-297">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)  
 [<span data-ttu-id="81242-298">Přehled LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="81242-298">LINQ to DataSet Overview</span></span>](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [<span data-ttu-id="81242-299">Dotazy na typové datové sady</span><span class="sxs-lookup"><span data-stu-id="81242-299">Querying Typed DataSets</span></span>](../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [<span data-ttu-id="81242-300">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="81242-300">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
