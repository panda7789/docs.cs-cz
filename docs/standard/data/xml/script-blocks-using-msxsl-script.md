---
title: 'Skript pomocí bloky msxsl: Script'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4d7dee9ebaed20970f715026661c29aae701289
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970627"
---
# <a name="script-blocks-using-msxslscript"></a><span data-ttu-id="1c720-102">Skript pomocí bloky msxsl: Script</span><span class="sxs-lookup"><span data-stu-id="1c720-102">Script Blocks Using msxsl:script</span></span>
<span data-ttu-id="1c720-103"><xref:System.Xml.Xsl.XslCompiledTransform> Třída podporuje vložené skripty pomocí `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="1c720-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports embedded scripts using the `msxsl:script` element.</span></span> <span data-ttu-id="1c720-104">Při načítání šablony stylů žádné definované funkce jsou kompilovaná Code Document Object Model (CodeDOM) pro jazyk Microsoft intermediate language (MSIL) a jsou spouštěny za běhu.</span><span class="sxs-lookup"><span data-stu-id="1c720-104">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by the Code Document Object Model (CodeDOM) and are executed during run time.</span></span> <span data-ttu-id="1c720-105">Sestavení vygenerované z bloku vloženého skriptu je oddělená než sestavení vygenerované pro šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="1c720-105">The assembly generated from the embedded script block is separate than the assembly generated for the style sheet.</span></span>  
  
## <a name="enable-xslt-script"></a><span data-ttu-id="1c720-106">Povolit skriptu XSLT</span><span class="sxs-lookup"><span data-stu-id="1c720-106">Enable XSLT Script</span></span>  
 <span data-ttu-id="1c720-107">Podpora pro vložené skripty je volitelné nastavení XSLT na <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="1c720-107">Support for embedded scripts is an optional XSLT setting on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="1c720-108">Ve výchozím nastavení je zakázána podpora skriptování.</span><span class="sxs-lookup"><span data-stu-id="1c720-108">Script support is disabled by default.</span></span> <span data-ttu-id="1c720-109">Povolení podpory skriptu, vytvořit <xref:System.Xml.Xsl.XsltSettings> objekt s <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> vlastnost nastavena na `true` a předejte objekt, který má <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="1c720-109">To enable script support, create an <xref:System.Xml.Xsl.XsltSettings> object with the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> property set to `true` and pass the object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c720-110">Pouze v případě, že budete potřebovat podporu skriptu a práci v plně důvěryhodném prostředí by měl být povoleno skriptování XSLT.</span><span class="sxs-lookup"><span data-stu-id="1c720-110">XSLT scripting should be enabled only if you require script support and you are working in a fully trusted environment.</span></span>  
  
## <a name="msxslscript-element-definition"></a><span data-ttu-id="1c720-111">msxsl: Script Element definice</span><span class="sxs-lookup"><span data-stu-id="1c720-111">msxsl:script Element Definition</span></span>  
 <span data-ttu-id="1c720-112">`msxsl:script` Element je rozšířením společnosti Microsoft pro XSLT 1.0 doporučení a obsahuje následující definice:</span><span class="sxs-lookup"><span data-stu-id="1c720-112">The `msxsl:script` element is a Microsoft extension to the XSLT 1.0 recommendation and has the following definition:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="1c720-113">`msxsl` Předpona je svázána s `urn:schemas-microsoft-com:xslt` identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1c720-113">The `msxsl` prefix is bound to the `urn:schemas-microsoft-com:xslt` namespace URI.</span></span> <span data-ttu-id="1c720-114">Šablona stylů musí zahrnovat `xmlns:msxsl=urn:schemas-microsoft-com:xslt` deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1c720-114">The style sheet must include the `xmlns:msxsl=urn:schemas-microsoft-com:xslt` namespace declaration.</span></span>  
  
 <span data-ttu-id="1c720-115">`language` Atribut je volitelný.</span><span class="sxs-lookup"><span data-stu-id="1c720-115">The `language` attribute is optional.</span></span> <span data-ttu-id="1c720-116">Jeho hodnota je jazyk kódu vloženého kódu bloku.</span><span class="sxs-lookup"><span data-stu-id="1c720-116">Its value is the code language of the embedded code block.</span></span> <span data-ttu-id="1c720-117">Jazyk je namapována na používání kompilátoru odpovídající CodeDOM <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="1c720-117">The language is mapped to the appropriate CodeDOM compiler using the <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1c720-118"><xref:System.Xml.Xsl.XslCompiledTransform> Třída může podporovat libovolný jazyk rozhraní Microsoft .NET, za předpokladu, že odpovídající zprostředkovatel je na počítači nainstalovaný a zaregistrovaný v oddíle system.codedom souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="1c720-118">The <xref:System.Xml.Xsl.XslCompiledTransform> class can support any Microsoft .NET language, assuming the appropriate provider is installed on the machine and is registered in the system.codedom section of the machine.config file.</span></span> <span data-ttu-id="1c720-119">Pokud `language` atribut není zadán, výchozí jazyk JScript.</span><span class="sxs-lookup"><span data-stu-id="1c720-119">If a `language` attribute is not specified, the language defaults to JScript.</span></span> <span data-ttu-id="1c720-120">Název jazyka není tak, aby byly ekvivalentní 'Jazyka JavaScript' a 'javascript: malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="1c720-120">The language name is not case-sensitive so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="1c720-121">`implements-prefix` Atribut je povinný.</span><span class="sxs-lookup"><span data-stu-id="1c720-121">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="1c720-122">Tento atribut se používá k deklarování oboru názvů a přidružte jej k bloku skriptu.</span><span class="sxs-lookup"><span data-stu-id="1c720-122">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="1c720-123">Hodnota tohoto atributu je předpona, která představuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="1c720-123">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="1c720-124">Tuto předponu lze definovat někde v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="1c720-124">This prefix can be defined somewhere in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c720-125">Při použití `msxsl:script` elementu, důrazně doporučujeme, aby skript, bez ohledu na jazyk, umístit do oddílu CDATA.</span><span class="sxs-lookup"><span data-stu-id="1c720-125">When using the `msxsl:script` element, we strongly recommend that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="1c720-126">Vzhledem k tomu, že skript může obsahovat operátory, identifikátory nebo oddělovače pro daný jazyk, pokud není obsažen v rámci oddílu CDATA, má potenciál je špatně interpretována jako XML.</span><span class="sxs-lookup"><span data-stu-id="1c720-126">Because the script can contain operators, identifiers, or delimiters for a given language, if it is not contained within a CDATA section, it has the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="1c720-127">Následující kód XML ukazuje šablonu oddílu CDATA umístění kódu.</span><span class="sxs-lookup"><span data-stu-id="1c720-127">The following XML shows a template of the CDATA section where code can be placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a><span data-ttu-id="1c720-128">Funkce skriptu</span><span class="sxs-lookup"><span data-stu-id="1c720-128">Script Functions</span></span>  
 <span data-ttu-id="1c720-129">Funkce mohou být deklarovány v rámci `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="1c720-129">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="1c720-130">Při deklaraci funkce, je obsažen v bloku skriptu.</span><span class="sxs-lookup"><span data-stu-id="1c720-130">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="1c720-131">Šablony stylů může obsahovat více blocích skriptu, každý operační nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="1c720-131">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="1c720-132">To znamená, že pokud jsou spuštěny uvnitř bloku skriptu, nelze volat funkci, která jste definovali v jiném bloku skriptu, pokud je deklarovaná mít stejný obor názvů a stejné skriptovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="1c720-132">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="1c720-133">Vzhledem k tomu, že každý blok skriptu může být v jeho vlastní jazyk a blok je analyzován podle pravidel gramatika tohoto analyzátoru jazyka doporučujeme použít správnou syntaxi jazyka používán.</span><span class="sxs-lookup"><span data-stu-id="1c720-133">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser we recommend that you use the correct syntax for the language in use.</span></span> <span data-ttu-id="1c720-134">Například pokud jste v bloku skriptu jazyka Microsoft C#, použijte syntaxi komentář jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="1c720-134">For example, if you are in a Microsoft C# script block, use the C# comment syntax.</span></span>  
  
 <span data-ttu-id="1c720-135">Zadané argumenty a návratové hodnoty funkce může být libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="1c720-135">The supplied arguments and return values to the function can be of any type.</span></span> <span data-ttu-id="1c720-136">Protože jsou typy W3C XPath podmnožiny běžných typů language runtime (CLR), převod typu se provádí na typy, které nejsou považovány za typem XPath.</span><span class="sxs-lookup"><span data-stu-id="1c720-136">Because the W3C XPath types are a subset of the common language runtime (CLR) types, type conversion takes place on types that are not considered to be an XPath type.</span></span> <span data-ttu-id="1c720-137">V následující tabulce jsou uvedeny odpovídající typy W3C a ekvivalentní typ CLR.</span><span class="sxs-lookup"><span data-stu-id="1c720-137">The following table shows the corresponding W3C types and the equivalent CLR type.</span></span>  
  
|<span data-ttu-id="1c720-138">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="1c720-138">W3C type</span></span>|<span data-ttu-id="1c720-139">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="1c720-139">CLR type</span></span>|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 <span data-ttu-id="1c720-140">Číselné typy CLR se převedou na <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="1c720-140">CLR numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="1c720-141"><xref:System.DateTime> Typ je převeden na <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="1c720-141">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="1c720-142"><xref:System.Xml.XPath.IXPathNavigable> typy budou převedené na <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="1c720-142"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="1c720-143">**[] Objektem XPathNavigator nastaveným na** je převedena na <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="1c720-143">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="1c720-144">Všechny ostatní typy vyvolat chybu.</span><span class="sxs-lookup"><span data-stu-id="1c720-144">All other types throw an error.</span></span>  
  
### <a name="importing-namespaces-and-assemblies"></a><span data-ttu-id="1c720-145">Importovat obory názvů a sestavení</span><span class="sxs-lookup"><span data-stu-id="1c720-145">Importing Namespaces and Assemblies</span></span>  
 <span data-ttu-id="1c720-146"><xref:System.Xml.Xsl.XslCompiledTransform> Třídy predefines sadu sestavení a obory názvů, které jsou podporovány ve výchozím nastavení `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="1c720-146">The <xref:System.Xml.Xsl.XslCompiledTransform> class predefines a set of assemblies and namespaces that are supported by default by the `msxsl:script` element.</span></span> <span data-ttu-id="1c720-147">Můžete však použít třídy a členy, které patří do oboru názvů, který není na seznamu předdefinovaných importováním sestavení a oboru názvů v `msxsl:script` bloku.</span><span class="sxs-lookup"><span data-stu-id="1c720-147">However, you can use classes and members belonging to a namespace that is not on the predefined list by importing the assembly and namespace in `msxsl:script` block.</span></span>  
  
#### <a name="assemblies"></a><span data-ttu-id="1c720-148">Sestavení</span><span class="sxs-lookup"><span data-stu-id="1c720-148">Assemblies</span></span>  
 <span data-ttu-id="1c720-149">Ve výchozím nastavení je odkazováno na následující dvě sestavení:</span><span class="sxs-lookup"><span data-stu-id="1c720-149">The following two assemblies are referenced by default:</span></span>  
  
-   <span data-ttu-id="1c720-150">System.dll</span><span class="sxs-lookup"><span data-stu-id="1c720-150">System.dll</span></span>  
  
-   <span data-ttu-id="1c720-151">System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="1c720-151">System.Xml.dll</span></span>  
  
-   <span data-ttu-id="1c720-152">Microsoft.VisualBasic.dll (je-li jazyk skriptu VB)</span><span class="sxs-lookup"><span data-stu-id="1c720-152">Microsoft.VisualBasic.dll (when the script language is VB)</span></span>  
  
 <span data-ttu-id="1c720-153">Můžete importovat další sestavení pomocí `msxsl:assembly` elementu.</span><span class="sxs-lookup"><span data-stu-id="1c720-153">You can import the additional assemblies using the `msxsl:assembly` element.</span></span> <span data-ttu-id="1c720-154">To zahrnuje sestavení při kompilaci šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="1c720-154">This includes the assembly when the style sheet is compiled.</span></span> <span data-ttu-id="1c720-155">`msxsl:assembly` Element má následující definice:</span><span class="sxs-lookup"><span data-stu-id="1c720-155">The `msxsl:assembly` element has the following definition:</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="1c720-156">`name` Atribut obsahuje název sestavení a `href` atribut obsahuje cestu k sestavení.</span><span class="sxs-lookup"><span data-stu-id="1c720-156">The `name` attribute contains the name of the assembly and the `href` attribute contains the path to the assembly.</span></span> <span data-ttu-id="1c720-157">Název sestavení může být úplný název, například "System.Data, verze = 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089", nebo krátký název, jako je například "System.Web".</span><span class="sxs-lookup"><span data-stu-id="1c720-157">The assembly name can be a full name, such as "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", or a short name, such as "System.Web".</span></span>  
  
#### <a name="namespaces"></a><span data-ttu-id="1c720-158">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="1c720-158">Namespaces</span></span>  
 <span data-ttu-id="1c720-159">Ve výchozím nastavení jsou zahrnuty následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="1c720-159">The following namespaces are included by default:</span></span>  
  
-   <span data-ttu-id="1c720-160">Systém</span><span class="sxs-lookup"><span data-stu-id="1c720-160">System</span></span>  
  
-   <span data-ttu-id="1c720-161">System.Collection</span><span class="sxs-lookup"><span data-stu-id="1c720-161">System.Collection</span></span>  
  
-   <span data-ttu-id="1c720-162">System.Text</span><span class="sxs-lookup"><span data-stu-id="1c720-162">System.Text</span></span>  
  
-   <span data-ttu-id="1c720-163">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="1c720-163">System.Text.RegularExpressions</span></span>  
  
-   <span data-ttu-id="1c720-164">System.Xml</span><span class="sxs-lookup"><span data-stu-id="1c720-164">System.Xml</span></span>  
  
-   <span data-ttu-id="1c720-165">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="1c720-165">System.Xml.Xsl</span></span>  
  
-   <span data-ttu-id="1c720-166">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="1c720-166">System.Xml.XPath</span></span>  
  
-   <span data-ttu-id="1c720-167">Microsoft.VisualBasic (je-li jazyk skriptu VB)</span><span class="sxs-lookup"><span data-stu-id="1c720-167">Microsoft.VisualBasic (when the script language is VB)</span></span>  
  
 <span data-ttu-id="1c720-168">Můžete přidat podporu pro další obory názvů pomocí `namespace` atribut.</span><span class="sxs-lookup"><span data-stu-id="1c720-168">You can add support for additional namespaces using the `namespace` attribute.</span></span> <span data-ttu-id="1c720-169">Hodnota atributu je název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1c720-169">The attribute value is the name of the namespace.</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a><span data-ttu-id="1c720-170">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c720-170">Example</span></span>  
 <span data-ttu-id="1c720-171">Následující příklad používá vložený skript k výpočtu obvod kruhu uveden jeho radius.</span><span class="sxs-lookup"><span data-stu-id="1c720-171">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a><span data-ttu-id="1c720-172">Number.XML</span><span class="sxs-lookup"><span data-stu-id="1c720-172">number.xml</span></span>  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a><span data-ttu-id="1c720-173">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="1c720-173">calc.xsl</span></span>  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="1c720-174">Výstup</span><span class="sxs-lookup"><span data-stu-id="1c720-174">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c720-175">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c720-175">See also</span></span>

- [<span data-ttu-id="1c720-176">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="1c720-176">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [<span data-ttu-id="1c720-177">Dynamické vytváření a kompilování zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="1c720-177">Dynamic Source Code Generation and Compilation</span></span>](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
