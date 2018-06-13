---
title: Msxsl:script bloky pomocí skriptu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23961caa7b307df46b20b3811d0883d4c702a357
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577160"
---
# <a name="script-blocks-using-msxslscript"></a><span data-ttu-id="3db5b-102">Msxsl:script bloky pomocí skriptu</span><span class="sxs-lookup"><span data-stu-id="3db5b-102">Script Blocks Using msxsl:script</span></span>
<span data-ttu-id="3db5b-103"><xref:System.Xml.Xsl.XslCompiledTransform> Třída podporuje vložené skripty pomocí `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="3db5b-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports embedded scripts using the `msxsl:script` element.</span></span> <span data-ttu-id="3db5b-104">Při načtení šablony stylů žádné definované funkce jsou kompilovaná do převodního jazyka Microsoft (MSIL) Code Document Object Model (CodeDOM) a jsou při běhu spuštěn.</span><span class="sxs-lookup"><span data-stu-id="3db5b-104">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by the Code Document Object Model (CodeDOM) and are executed during run time.</span></span> <span data-ttu-id="3db5b-105">Sestavení vygenerovat z bloku vloženého skriptu je samostatný než sestavení vygenerované šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="3db5b-105">The assembly generated from the embedded script block is separate than the assembly generated for the style sheet.</span></span>  
  
## <a name="enable-xslt-script"></a><span data-ttu-id="3db5b-106">Povolit XSLT skriptů</span><span class="sxs-lookup"><span data-stu-id="3db5b-106">Enable XSLT Script</span></span>  
 <span data-ttu-id="3db5b-107">Podpora pro vložené skripty je volitelné nastavení XSLT na <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="3db5b-107">Support for embedded scripts is an optional XSLT setting on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="3db5b-108">Podpora skriptování ve výchozím nastavení vypnutá.</span><span class="sxs-lookup"><span data-stu-id="3db5b-108">Script support is disabled by default.</span></span> <span data-ttu-id="3db5b-109">Chcete-li povolit podporu skript, vytvořit <xref:System.Xml.Xsl.XsltSettings> objektu s <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> vlastnost nastavena na hodnotu `true` a předat objekt, který má <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="3db5b-109">To enable script support, create an <xref:System.Xml.Xsl.XsltSettings> object with the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> property set to `true` and pass the object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3db5b-110">Pouze v případě, že budete potřebovat podporu skriptu a práci ve plně důvěryhodný pro prostředí by měl být povoleno skriptování XSLT.</span><span class="sxs-lookup"><span data-stu-id="3db5b-110">XSLT scripting should be enabled only if you require script support and you are working in a fully trusted environment.</span></span>  
  
## <a name="msxslscript-element-definition"></a><span data-ttu-id="3db5b-111">msxsl:Script definice elementu</span><span class="sxs-lookup"><span data-stu-id="3db5b-111">msxsl:script Element Definition</span></span>  
 <span data-ttu-id="3db5b-112">`msxsl:script` Element rozšíření Microsoft pro XSLT 1.0 doporučení a má následující definice:</span><span class="sxs-lookup"><span data-stu-id="3db5b-112">The `msxsl:script` element is a Microsoft extension to the XSLT 1.0 recommendation and has the following definition:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="3db5b-113">`msxsl` Předpona je vázána `urn:schemas-microsoft-com:xslt` identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3db5b-113">The `msxsl` prefix is bound to the `urn:schemas-microsoft-com:xslt` namespace URI.</span></span> <span data-ttu-id="3db5b-114">Musí zahrnovat šablony stylů `xmlns:msxsl=urn:schemas-microsoft-com:xslt` deklaraci oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3db5b-114">The style sheet must include the `xmlns:msxsl=urn:schemas-microsoft-com:xslt` namespace declaration.</span></span>  
  
 <span data-ttu-id="3db5b-115">`language` Atribut je volitelný.</span><span class="sxs-lookup"><span data-stu-id="3db5b-115">The `language` attribute is optional.</span></span> <span data-ttu-id="3db5b-116">Jeho hodnota může být jazyk kódu vloženého kódu bloku.</span><span class="sxs-lookup"><span data-stu-id="3db5b-116">Its value is the code language of the embedded code block.</span></span> <span data-ttu-id="3db5b-117">Jazyk je namapována na odpovídající pomocí modelu CodeDOM kompilátoru <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="3db5b-117">The language is mapped to the appropriate CodeDOM compiler using the <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3db5b-118"><xref:System.Xml.Xsl.XslCompiledTransform> Třída může podporovat všechny jazykové rozhraní Microsoft .NET, za předpokladu, že příslušného poskytovatele je nainstalovaná na počítači a je zaregistrovaný v oddílu system.codedom souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="3db5b-118">The <xref:System.Xml.Xsl.XslCompiledTransform> class can support any Microsoft .NET language, assuming the appropriate provider is installed on the machine and is registered in the system.codedom section of the machine.config file.</span></span> <span data-ttu-id="3db5b-119">Pokud `language` atribut nezadá, výchozí jazyk JScript.</span><span class="sxs-lookup"><span data-stu-id="3db5b-119">If a `language` attribute is not specified, the language defaults to JScript.</span></span> <span data-ttu-id="3db5b-120">Název jazyka není malá a velká písmena, takže odpovídají 'JavaScript' a "javascript".</span><span class="sxs-lookup"><span data-stu-id="3db5b-120">The language name is not case-sensitive so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="3db5b-121">`implements-prefix` Atribut je povinný.</span><span class="sxs-lookup"><span data-stu-id="3db5b-121">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="3db5b-122">Tento atribut slouží k deklarace oboru názvů a přidružte ji k blok skriptu.</span><span class="sxs-lookup"><span data-stu-id="3db5b-122">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="3db5b-123">Hodnota tohoto atributu je předpona, která představuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="3db5b-123">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="3db5b-124">Tato předpona může být definováno někde v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="3db5b-124">This prefix can be defined somewhere in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3db5b-125">Při použití `msxsl:script` elementu, důrazně doporučujeme, aby na skript, bez ohledu na jazyk, být umístěna uvnitř oddílu CDATA.</span><span class="sxs-lookup"><span data-stu-id="3db5b-125">When using the `msxsl:script` element, we strongly recommend that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="3db5b-126">Vzhledem k tomu, že skript může obsahovat operátory, identifikátory nebo oddělovače pro daný jazyk, pokud není obsažen v rámci oddílu CDATA, má potenciál se k nesprávné interpretaci jako XML.</span><span class="sxs-lookup"><span data-stu-id="3db5b-126">Because the script can contain operators, identifiers, or delimiters for a given language, if it is not contained within a CDATA section, it has the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="3db5b-127">Následující kód XML ukazuje šablonu oddílu CDATA umístění kódu.</span><span class="sxs-lookup"><span data-stu-id="3db5b-127">The following XML shows a template of the CDATA section where code can be placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a><span data-ttu-id="3db5b-128">Funkce skriptu</span><span class="sxs-lookup"><span data-stu-id="3db5b-128">Script Functions</span></span>  
 <span data-ttu-id="3db5b-129">Funkce můžete deklarované v rámci `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="3db5b-129">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="3db5b-130">Pokud je deklarovaná funkci, je obsažený v bloku skriptu.</span><span class="sxs-lookup"><span data-stu-id="3db5b-130">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="3db5b-131">Šablony stylů může obsahovat více skriptu bloků, každý operační nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="3db5b-131">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="3db5b-132">To znamená, že pokud spouštění uvnitř bloku skriptu nelze volat funkci, která jste definovali v jiného bloku skriptu, pokud je deklarovaná do mají stejný obor názvů a stejný skriptovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="3db5b-132">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="3db5b-133">Protože každý blok skriptu může být v jeho vlastní jazyk a bloku je analyzována podle pravidel gramatika objektů tohoto analyzátoru jazyka doporučujeme používáte správnou syntaxi pro jazyk používán.</span><span class="sxs-lookup"><span data-stu-id="3db5b-133">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser we recommend that you use the correct syntax for the language in use.</span></span> <span data-ttu-id="3db5b-134">Pokud jste v bloku skriptu Microsoft C#, například pomocí syntaxe komentáře jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="3db5b-134">For example, if you are in a Microsoft C# script block, use the C# comment syntax.</span></span>  
  
 <span data-ttu-id="3db5b-135">Zadané argumenty a návratové hodnoty funkce můžou být jakéhokoli typu.</span><span class="sxs-lookup"><span data-stu-id="3db5b-135">The supplied arguments and return values to the function can be of any type.</span></span> <span data-ttu-id="3db5b-136">Protože se typy W3C XPath podmnožinu běžné typy language runtime (CLR), typ převodu dojde na typy, které nejsou považovány za typ XPath.</span><span class="sxs-lookup"><span data-stu-id="3db5b-136">Because the W3C XPath types are a subset of the common language runtime (CLR) types, type conversion takes place on types that are not considered to be an XPath type.</span></span> <span data-ttu-id="3db5b-137">Následující tabulka uvádí odpovídající typy W3C a ekvivalentní typ CLR.</span><span class="sxs-lookup"><span data-stu-id="3db5b-137">The following table shows the corresponding W3C types and the equivalent CLR type.</span></span>  
  
|<span data-ttu-id="3db5b-138">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="3db5b-138">W3C type</span></span>|<span data-ttu-id="3db5b-139">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="3db5b-139">CLR type</span></span>|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 <span data-ttu-id="3db5b-140">Číselné typy CLR se převedou na <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="3db5b-140">CLR numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="3db5b-141"><xref:System.DateTime> Typ je převeden na <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3db5b-141">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="3db5b-142"><xref:System.Xml.XPath.IXPathNavigable> typy budou převedené na <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="3db5b-142"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="3db5b-143">**[] Objektem XPathNavigator nastaveným na** jsou převedeny na <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="3db5b-143">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="3db5b-144">Všechny ostatní typy vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="3db5b-144">All other types throw an error.</span></span>  
  
### <a name="importing-namespaces-and-assemblies"></a><span data-ttu-id="3db5b-145">Import obory názvů a sestavení</span><span class="sxs-lookup"><span data-stu-id="3db5b-145">Importing Namespaces and Assemblies</span></span>  
 <span data-ttu-id="3db5b-146"><xref:System.Xml.Xsl.XslCompiledTransform> Třída predefines sadu sestavení a obory názvů, které jsou podporovány ve výchozím nastavení `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="3db5b-146">The <xref:System.Xml.Xsl.XslCompiledTransform> class predefines a set of assemblies and namespaces that are supported by default by the `msxsl:script` element.</span></span> <span data-ttu-id="3db5b-147">Můžete však použít třídy a členové, které patří do oboru názvů, který není v seznamu předdefinovaných importováním sestavení a oboru názvů v `msxsl:script` bloku.</span><span class="sxs-lookup"><span data-stu-id="3db5b-147">However, you can use classes and members belonging to a namespace that is not on the predefined list by importing the assembly and namespace in `msxsl:script` block.</span></span>  
  
#### <a name="assemblies"></a><span data-ttu-id="3db5b-148">Sestavení</span><span class="sxs-lookup"><span data-stu-id="3db5b-148">Assemblies</span></span>  
 <span data-ttu-id="3db5b-149">Ve výchozím nastavení se odkazuje na následující dvě sestavení:</span><span class="sxs-lookup"><span data-stu-id="3db5b-149">The following two assemblies are referenced by default:</span></span>  
  
-   <span data-ttu-id="3db5b-150">System.dll</span><span class="sxs-lookup"><span data-stu-id="3db5b-150">System.dll</span></span>  
  
-   <span data-ttu-id="3db5b-151">System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="3db5b-151">System.Xml.dll</span></span>  
  
-   <span data-ttu-id="3db5b-152">Souboru Microsoft.VisualBasic.dll (Pokud jazyk skript jazyka Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3db5b-152">Microsoft.VisualBasic.dll (when the script language is VB)</span></span>  
  
 <span data-ttu-id="3db5b-153">Můžete importovat další sestavení pomocí `msxsl:assembly` elementu.</span><span class="sxs-lookup"><span data-stu-id="3db5b-153">You can import the additional assemblies using the `msxsl:assembly` element.</span></span> <span data-ttu-id="3db5b-154">To zahrnuje sestavení při kompilaci šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="3db5b-154">This includes the assembly when the style sheet is compiled.</span></span> <span data-ttu-id="3db5b-155">`msxsl:assembly` Element má následující definice:</span><span class="sxs-lookup"><span data-stu-id="3db5b-155">The `msxsl:assembly` element has the following definition:</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="3db5b-156">`name` Atribut obsahuje název sestavení a `href` atribut obsahuje cestu k sestavení.</span><span class="sxs-lookup"><span data-stu-id="3db5b-156">The `name` attribute contains the name of the assembly and the `href` attribute contains the path to the assembly.</span></span> <span data-ttu-id="3db5b-157">Název sestavení může být úplný název, například "System.Data, verze = 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089", nebo krátký název, jako je například "System.Web".</span><span class="sxs-lookup"><span data-stu-id="3db5b-157">The assembly name can be a full name, such as "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", or a short name, such as "System.Web".</span></span>  
  
#### <a name="namespaces"></a><span data-ttu-id="3db5b-158">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="3db5b-158">Namespaces</span></span>  
 <span data-ttu-id="3db5b-159">Ve výchozím nastavení jsou zahrnuty následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="3db5b-159">The following namespaces are included by default:</span></span>  
  
-   <span data-ttu-id="3db5b-160">Systém</span><span class="sxs-lookup"><span data-stu-id="3db5b-160">System</span></span>  
  
-   <span data-ttu-id="3db5b-161">System.Collection</span><span class="sxs-lookup"><span data-stu-id="3db5b-161">System.Collection</span></span>  
  
-   <span data-ttu-id="3db5b-162">System.Text</span><span class="sxs-lookup"><span data-stu-id="3db5b-162">System.Text</span></span>  
  
-   <span data-ttu-id="3db5b-163">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="3db5b-163">System.Text.RegularExpressions</span></span>  
  
-   <span data-ttu-id="3db5b-164">System.Xml</span><span class="sxs-lookup"><span data-stu-id="3db5b-164">System.Xml</span></span>  
  
-   <span data-ttu-id="3db5b-165">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="3db5b-165">System.Xml.Xsl</span></span>  
  
-   <span data-ttu-id="3db5b-166">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="3db5b-166">System.Xml.XPath</span></span>  
  
-   <span data-ttu-id="3db5b-167">Microsoft.VisualBasic (Pokud jazyk skript jazyka Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3db5b-167">Microsoft.VisualBasic (when the script language is VB)</span></span>  
  
 <span data-ttu-id="3db5b-168">Můžete přidat podporu pro další obory názvů pomocí `namespace` atribut.</span><span class="sxs-lookup"><span data-stu-id="3db5b-168">You can add support for additional namespaces using the `namespace` attribute.</span></span> <span data-ttu-id="3db5b-169">Hodnota atributu je název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3db5b-169">The attribute value is the name of the namespace.</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a><span data-ttu-id="3db5b-170">Příklad</span><span class="sxs-lookup"><span data-stu-id="3db5b-170">Example</span></span>  
 <span data-ttu-id="3db5b-171">Následující příklad používá k výpočtu obvodu kruhu zadané jeho radius vloženého skriptu.</span><span class="sxs-lookup"><span data-stu-id="3db5b-171">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a><span data-ttu-id="3db5b-172">Number.XML</span><span class="sxs-lookup"><span data-stu-id="3db5b-172">number.xml</span></span>  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a><span data-ttu-id="3db5b-173">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="3db5b-173">calc.xsl</span></span>  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="3db5b-174">Výstup</span><span class="sxs-lookup"><span data-stu-id="3db5b-174">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3db5b-175">Viz také</span><span class="sxs-lookup"><span data-stu-id="3db5b-175">See Also</span></span>  
 [<span data-ttu-id="3db5b-176">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="3db5b-176">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="3db5b-177">Dynamické vytváření a kompilování zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="3db5b-177">Dynamic Source Code Generation and Compilation</span></span>](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
