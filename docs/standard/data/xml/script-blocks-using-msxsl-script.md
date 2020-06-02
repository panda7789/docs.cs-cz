---
title: Bloky skriptu používající element msxsl:script
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
ms.openlocfilehash: e65308f097e81d844cb04b1ebd5cbcdd8a3aadad
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291991"
---
# <a name="script-blocks-using-msxslscript"></a><span data-ttu-id="bdac0-102">Bloky skriptu používající element msxsl:script</span><span class="sxs-lookup"><span data-stu-id="bdac0-102">Script Blocks Using msxsl:script</span></span>
<span data-ttu-id="bdac0-103"><xref:System.Xml.Xsl.XslCompiledTransform>Třída podporuje vložené skripty pomocí `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="bdac0-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports embedded scripts using the `msxsl:script` element.</span></span> <span data-ttu-id="bdac0-104">Při načtení předlohy se styly jsou všechny definované funkce kompilovány do jazyka MSIL (Microsoft Intermediate Language) pomocí Code Document Object Model (CodeDOM) a jsou prováděny během doby běhu.</span><span class="sxs-lookup"><span data-stu-id="bdac0-104">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by the Code Document Object Model (CodeDOM) and are executed during run time.</span></span> <span data-ttu-id="bdac0-105">Sestavení vygenerované z vloženého bloku skriptu je oddělené od sestavení generovaného pro šablonu stylů.</span><span class="sxs-lookup"><span data-stu-id="bdac0-105">The assembly generated from the embedded script block is separate than the assembly generated for the style sheet.</span></span>  
  
## <a name="enable-xslt-script"></a><span data-ttu-id="bdac0-106">Povolit skript XSLT</span><span class="sxs-lookup"><span data-stu-id="bdac0-106">Enable XSLT Script</span></span>  
 <span data-ttu-id="bdac0-107">Podpora pro vložené skripty je volitelné nastavení XSLT pro <xref:System.Xml.Xsl.XslCompiledTransform> třídu.</span><span class="sxs-lookup"><span data-stu-id="bdac0-107">Support for embedded scripts is an optional XSLT setting on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="bdac0-108">Podpora skriptů je ve výchozím nastavení zakázaná.</span><span class="sxs-lookup"><span data-stu-id="bdac0-108">Script support is disabled by default.</span></span> <span data-ttu-id="bdac0-109">Chcete-li povolit podporu skriptů, vytvořte <xref:System.Xml.Xsl.XsltSettings> objekt s <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> vlastností nastavenou na `true` a předejte objekt <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="bdac0-109">To enable script support, create an <xref:System.Xml.Xsl.XsltSettings> object with the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> property set to `true` and pass the object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdac0-110">Skriptování XSLT by mělo být povoleno pouze v případě, že potřebujete podporu skriptů a pracujete v plně důvěryhodném prostředí.</span><span class="sxs-lookup"><span data-stu-id="bdac0-110">XSLT scripting should be enabled only if you require script support and you are working in a fully trusted environment.</span></span>  
  
## <a name="msxslscript-element-definition"></a><span data-ttu-id="bdac0-111">msxsl: definice elementu skriptu</span><span class="sxs-lookup"><span data-stu-id="bdac0-111">msxsl:script Element Definition</span></span>  
 <span data-ttu-id="bdac0-112">`msxsl:script`Element je rozšířením společnosti Microsoft k doporučení XSLT 1,0 a má následující definici:</span><span class="sxs-lookup"><span data-stu-id="bdac0-112">The `msxsl:script` element is a Microsoft extension to the XSLT 1.0 recommendation and has the following definition:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="bdac0-113">`msxsl`Předpona je svázána s `urn:schemas-microsoft-com:xslt` identifikátorem URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bdac0-113">The `msxsl` prefix is bound to the `urn:schemas-microsoft-com:xslt` namespace URI.</span></span> <span data-ttu-id="bdac0-114">Šablona stylů musí zahrnovat `xmlns:msxsl=urn:schemas-microsoft-com:xslt` deklaraci oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bdac0-114">The style sheet must include the `xmlns:msxsl=urn:schemas-microsoft-com:xslt` namespace declaration.</span></span>  
  
 <span data-ttu-id="bdac0-115">`language`Atribut je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="bdac0-115">The `language` attribute is optional.</span></span> <span data-ttu-id="bdac0-116">Jeho hodnota je jazyk kódu vloženého bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="bdac0-116">Its value is the code language of the embedded code block.</span></span> <span data-ttu-id="bdac0-117">Jazyk je namapován na příslušný kompilátor CodeDOM pomocí <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="bdac0-117">The language is mapped to the appropriate CodeDOM compiler using the <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bdac0-118"><xref:System.Xml.Xsl.XslCompiledTransform>Třída může podporovat libovolný jazyk platformy Microsoft .NET. za předpokladu, že příslušný zprostředkovatel je nainstalován v počítači a je zaregistrován v oddílu System. CodeDom souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="bdac0-118">The <xref:System.Xml.Xsl.XslCompiledTransform> class can support any Microsoft .NET language, assuming the appropriate provider is installed on the machine and is registered in the system.codedom section of the machine.config file.</span></span> <span data-ttu-id="bdac0-119">Pokud `language` atribut není zadán, výchozí jazyk je JScript.</span><span class="sxs-lookup"><span data-stu-id="bdac0-119">If a `language` attribute is not specified, the language defaults to JScript.</span></span> <span data-ttu-id="bdac0-120">V názvu jazyka se nerozlišují velká a malá písmena, takže jazyky JavaScript a JavaScript jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="bdac0-120">The language name is not case-sensitive so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="bdac0-121">`implements-prefix`Atribut je povinný.</span><span class="sxs-lookup"><span data-stu-id="bdac0-121">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="bdac0-122">Tento atribut slouží k deklaraci oboru názvů a k jeho přidružení ke bloku skriptu.</span><span class="sxs-lookup"><span data-stu-id="bdac0-122">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="bdac0-123">Hodnota tohoto atributu je předpona, která představuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="bdac0-123">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="bdac0-124">Tuto předponu lze definovat někde v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="bdac0-124">This prefix can be defined somewhere in a style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdac0-125">Při použití `msxsl:script` prvku důrazně doporučujeme, aby byl skript bez ohledu na jazyk umístěn uvnitř oddílu CDATA.</span><span class="sxs-lookup"><span data-stu-id="bdac0-125">When using the `msxsl:script` element, we strongly recommend that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="bdac0-126">Vzhledem k tomu, že skript může obsahovat operátory, identifikátory nebo oddělovače pro daný jazyk, pokud není obsažen v oddílu CDATA, má potenciál, který je špatně interpretován jako XML.</span><span class="sxs-lookup"><span data-stu-id="bdac0-126">Because the script can contain operators, identifiers, or delimiters for a given language, if it is not contained within a CDATA section, it has the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="bdac0-127">Následující kód XML ukazuje šablonu oddílu CDATA, kde lze umístit kód.</span><span class="sxs-lookup"><span data-stu-id="bdac0-127">The following XML shows a template of the CDATA section where code can be placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a><span data-ttu-id="bdac0-128">Funkce skriptu</span><span class="sxs-lookup"><span data-stu-id="bdac0-128">Script Functions</span></span>  
 <span data-ttu-id="bdac0-129">Funkce mohou být deklarovány v rámci `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="bdac0-129">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="bdac0-130">Je-li funkce deklarována, je obsažena v bloku skriptu.</span><span class="sxs-lookup"><span data-stu-id="bdac0-130">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="bdac0-131">Šablony stylů mohou obsahovat více bloků skriptu, z nichž každý pracuje nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="bdac0-131">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="bdac0-132">To znamená, že pokud provádíte uvnitř bloku skriptu, nemůžete volat funkci, která je definována v jiném bloku skriptu, pokud není deklarována tak, aby měla stejný obor názvů a stejný skriptovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="bdac0-132">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="bdac0-133">Vzhledem k tomu, že každý blok skriptu může být ve vlastním jazyce a blok je analyzován podle gramatických pravidel daného jazykového analyzátoru, doporučujeme použít správnou syntaxi používaného jazyka.</span><span class="sxs-lookup"><span data-stu-id="bdac0-133">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser we recommend that you use the correct syntax for the language in use.</span></span> <span data-ttu-id="bdac0-134">Například pokud jste v bloku skriptu Microsoft C#, použijte syntaxi komentářů jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="bdac0-134">For example, if you are in a Microsoft C# script block, use the C# comment syntax.</span></span>  
  
 <span data-ttu-id="bdac0-135">Zadané argumenty a návratové hodnoty funkce mohou být libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="bdac0-135">The supplied arguments and return values to the function can be of any type.</span></span> <span data-ttu-id="bdac0-136">Vzhledem k tomu, že typy XPath W3C jsou podmnožinou typů modulu CLR (Common Language Runtime), převod typu probíhá u typů, které nejsou považovány za typ XPath.</span><span class="sxs-lookup"><span data-stu-id="bdac0-136">Because the W3C XPath types are a subset of the common language runtime (CLR) types, type conversion takes place on types that are not considered to be an XPath type.</span></span> <span data-ttu-id="bdac0-137">V následující tabulce jsou uvedeny odpovídající typy W3C a ekvivalentní typ CLR.</span><span class="sxs-lookup"><span data-stu-id="bdac0-137">The following table shows the corresponding W3C types and the equivalent CLR type.</span></span>  
  
|<span data-ttu-id="bdac0-138">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="bdac0-138">W3C type</span></span>|<span data-ttu-id="bdac0-139">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="bdac0-139">CLR type</span></span>|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 <span data-ttu-id="bdac0-140">Číselné typy CLR jsou převedeny na <xref:System.Double> .</span><span class="sxs-lookup"><span data-stu-id="bdac0-140">CLR numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="bdac0-141"><xref:System.DateTime>Typ je převeden na <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="bdac0-141">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="bdac0-142"><xref:System.Xml.XPath.IXPathNavigable>typy jsou převedeny na <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="bdac0-142"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="bdac0-143">**Prvek XPathNavigator []** je převeden na <xref:System.Xml.XPath.XPathNodeIterator> .</span><span class="sxs-lookup"><span data-stu-id="bdac0-143">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="bdac0-144">Všechny ostatní typy vyvolávají chybu.</span><span class="sxs-lookup"><span data-stu-id="bdac0-144">All other types throw an error.</span></span>  
  
### <a name="importing-namespaces-and-assemblies"></a><span data-ttu-id="bdac0-145">Import oborů názvů a sestavení</span><span class="sxs-lookup"><span data-stu-id="bdac0-145">Importing Namespaces and Assemblies</span></span>  
 <span data-ttu-id="bdac0-146"><xref:System.Xml.Xsl.XslCompiledTransform>Třída předdefinuje sadu sestavení a oborů názvů, které jsou ve výchozím nastavení podporovány `msxsl:script` prvkem.</span><span class="sxs-lookup"><span data-stu-id="bdac0-146">The <xref:System.Xml.Xsl.XslCompiledTransform> class predefines a set of assemblies and namespaces that are supported by default by the `msxsl:script` element.</span></span> <span data-ttu-id="bdac0-147">Můžete však použít třídy a členy patřící do oboru názvů, který není v předdefinovaném seznamu importováním sestavení a oboru názvů v `msxsl:script` bloku.</span><span class="sxs-lookup"><span data-stu-id="bdac0-147">However, you can use classes and members belonging to a namespace that is not on the predefined list by importing the assembly and namespace in `msxsl:script` block.</span></span>  
  
#### <a name="assemblies"></a><span data-ttu-id="bdac0-148">Sestavení</span><span class="sxs-lookup"><span data-stu-id="bdac0-148">Assemblies</span></span>  
 <span data-ttu-id="bdac0-149">Ve výchozím nastavení je odkazováno na následující dvě sestavení:</span><span class="sxs-lookup"><span data-stu-id="bdac0-149">The following two assemblies are referenced by default:</span></span>  
  
- <span data-ttu-id="bdac0-150">System.dll</span><span class="sxs-lookup"><span data-stu-id="bdac0-150">System.dll</span></span>  
  
- <span data-ttu-id="bdac0-151">System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="bdac0-151">System.Xml.dll</span></span>  
  
- <span data-ttu-id="bdac0-152">Microsoft. VisualBasic. dll (Pokud je jazyk skriptu VB)</span><span class="sxs-lookup"><span data-stu-id="bdac0-152">Microsoft.VisualBasic.dll (when the script language is VB)</span></span>  
  
 <span data-ttu-id="bdac0-153">Můžete importovat další sestavení pomocí `msxsl:assembly` elementu.</span><span class="sxs-lookup"><span data-stu-id="bdac0-153">You can import the additional assemblies using the `msxsl:assembly` element.</span></span> <span data-ttu-id="bdac0-154">To zahrnuje sestavení při kompilování předlohy se styly.</span><span class="sxs-lookup"><span data-stu-id="bdac0-154">This includes the assembly when the style sheet is compiled.</span></span> <span data-ttu-id="bdac0-155">`msxsl:assembly`Element má následující definici:</span><span class="sxs-lookup"><span data-stu-id="bdac0-155">The `msxsl:assembly` element has the following definition:</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="bdac0-156">`name`Atribut obsahuje název sestavení a `href` atribut obsahuje cestu k sestavení.</span><span class="sxs-lookup"><span data-stu-id="bdac0-156">The `name` attribute contains the name of the assembly and the `href` attribute contains the path to the assembly.</span></span> <span data-ttu-id="bdac0-157">Název sestavení může být úplný název, například "System. data, Version = 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089" nebo krátký název, například "System. Web".</span><span class="sxs-lookup"><span data-stu-id="bdac0-157">The assembly name can be a full name, such as "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", or a short name, such as "System.Web".</span></span>  
  
#### <a name="namespaces"></a><span data-ttu-id="bdac0-158">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="bdac0-158">Namespaces</span></span>  
 <span data-ttu-id="bdac0-159">Ve výchozím nastavení jsou zahrnuty následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="bdac0-159">The following namespaces are included by default:</span></span>  
  
- <span data-ttu-id="bdac0-160">Systém</span><span class="sxs-lookup"><span data-stu-id="bdac0-160">System</span></span>  
  
- <span data-ttu-id="bdac0-161">System.Collection</span><span class="sxs-lookup"><span data-stu-id="bdac0-161">System.Collection</span></span>  
  
- <span data-ttu-id="bdac0-162">System.Text</span><span class="sxs-lookup"><span data-stu-id="bdac0-162">System.Text</span></span>  
  
- <span data-ttu-id="bdac0-163">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="bdac0-163">System.Text.RegularExpressions</span></span>  
  
- <span data-ttu-id="bdac0-164">System.Xml</span><span class="sxs-lookup"><span data-stu-id="bdac0-164">System.Xml</span></span>  
  
- <span data-ttu-id="bdac0-165">System. XML. xsl</span><span class="sxs-lookup"><span data-stu-id="bdac0-165">System.Xml.Xsl</span></span>  
  
- <span data-ttu-id="bdac0-166">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="bdac0-166">System.Xml.XPath</span></span>  
  
- <span data-ttu-id="bdac0-167">Microsoft. VisualBasic (Pokud je skriptovací jazyk VB)</span><span class="sxs-lookup"><span data-stu-id="bdac0-167">Microsoft.VisualBasic (when the script language is VB)</span></span>  
  
 <span data-ttu-id="bdac0-168">Podporu pro další obory názvů můžete přidat pomocí `namespace` atributu.</span><span class="sxs-lookup"><span data-stu-id="bdac0-168">You can add support for additional namespaces using the `namespace` attribute.</span></span> <span data-ttu-id="bdac0-169">Hodnota atributu je název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bdac0-169">The attribute value is the name of the namespace.</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a><span data-ttu-id="bdac0-170">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdac0-170">Example</span></span>  
 <span data-ttu-id="bdac0-171">V následujícím příkladu je použit vložený skript k výpočtu obvodu kružnice s daným poloměrem.</span><span class="sxs-lookup"><span data-stu-id="bdac0-171">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a><span data-ttu-id="bdac0-172">Number. XML</span><span class="sxs-lookup"><span data-stu-id="bdac0-172">number.xml</span></span>  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a><span data-ttu-id="bdac0-173">Calc. xsl</span><span class="sxs-lookup"><span data-stu-id="bdac0-173">calc.xsl</span></span>  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="bdac0-174">Výstup</span><span class="sxs-lookup"><span data-stu-id="bdac0-174">Output</span></span>  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bdac0-175">Viz také</span><span class="sxs-lookup"><span data-stu-id="bdac0-175">See also</span></span>

- [<span data-ttu-id="bdac0-176">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="bdac0-176">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="bdac0-177">Generování a kompilace dynamického zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="bdac0-177">Dynamic Source Code Generation and Compilation</span></span>](../../../framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
