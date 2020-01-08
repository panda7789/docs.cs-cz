---
title: Skriptování šablon stylů XSLT pomocí <msxsl:script >
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32695d3bc29693ab4cf1e2f9d721d35598ecfb86
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344710"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a><span data-ttu-id="b5e9b-102">Skriptování šablony stylů XSLT pomocí \<msxsl: > skriptu</span><span class="sxs-lookup"><span data-stu-id="b5e9b-102">XSLT Stylesheet Scripting Using \<msxsl:script></span></span>
<span data-ttu-id="b5e9b-103">Třída <xref:System.Xml.Xsl.XslTransform> podporuje vložené skriptování pomocí elementu `script`.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-103">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5e9b-104">Třída <xref:System.Xml.Xsl.XslTransform> je v .NET Framework 2,0 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="b5e9b-105">Pomocí třídy <xref:System.Xml.Xsl.XslCompiledTransform> můžete provádět transformace XSLT (Extensible Stylesheet Language).</span><span class="sxs-lookup"><span data-stu-id="b5e9b-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="b5e9b-106">Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="b5e9b-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="b5e9b-107">Třída <xref:System.Xml.Xsl.XslTransform> podporuje vložené skriptování pomocí elementu `script`.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-107">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="b5e9b-108">Při načtení předlohy se styly se všechny definované funkce zkompiluje do jazyka MSIL (Microsoft Intermediate Language) zabalením do definice třídy a nedochází v důsledku ztráty výkonu.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-108">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="b5e9b-109">`<msxsl:script>` element je definován níže:</span><span class="sxs-lookup"><span data-stu-id="b5e9b-109">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="b5e9b-110">kde `msxsl` je předpona svázaná s oborem názvů `urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-110">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="b5e9b-111">Atribut `language` není povinný, ale pokud je zadaný, musí být jeho hodnota jedna z následujících hodnot: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`nebo `CSharp`.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-111">The `language` attribute is not mandatory, but if specified, its value must be one of the following: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`, or `CSharp`.</span></span> <span data-ttu-id="b5e9b-112">Pokud není zadaný, použije se výchozí jazyk JScript.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-112">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="b5e9b-113">U `language-name` se nerozlišují velká a malá písmena, takže JavaScript a JavaScript jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-113">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="b5e9b-114">Atribut `implements-prefix` je povinný.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-114">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="b5e9b-115">Tento atribut slouží k deklaraci oboru názvů a k jeho přidružení ke bloku skriptu.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-115">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="b5e9b-116">Hodnota tohoto atributu je předpona, která představuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-116">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="b5e9b-117">Tento obor názvů lze definovat někde v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-117">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="b5e9b-118">Vzhledem k tomu, že element `msxsl:script` patří do `urn:schemas-microsoft-com:xslt`oboru názvů, šablona stylů musí zahrnovat deklaraci oboru názvů `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-118">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="b5e9b-119">Pokud volajícímu skriptu nemáte oprávnění k přístupu <xref:System.Security.Permissions.SecurityPermissionFlag>, skript v šabloně stylů nebude nikdy zkompilován a volání <xref:System.Xml.Xsl.XslTransform.Load%2A> se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-119">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="b5e9b-120">Pokud má volající oprávnění `UnmanagedCode`, skript se zkompiluje, ale operace, které jsou povoleny, jsou závislé na legitimaci, která je zadána v době načítání.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-120">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="b5e9b-121">Pokud používáte jednu z <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, které přebírají <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XPath.XPathNavigator> pro načtení předlohy se styly, je nutné použít přetížení <xref:System.Xml.Xsl.XslTransform.Load%2A>, které přijímá parametr <xref:System.Security.Policy.Evidence> jako jeden z jeho argumentů.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-121">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="b5e9b-122">Aby mohl volající poskytnout legitimaci, musí mít <xref:System.Security.Permissions.SecurityPermissionFlag> oprávnění, aby mohl poskytnout `Evidence` pro sestavení skriptu.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-122">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="b5e9b-123">Pokud volající nemá toto oprávnění, může nastavit parametr `Evidence` na hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-123">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="b5e9b-124">Způsobí to, že funkce <xref:System.Xml.Xsl.XslTransform.Load%2A> selže, pokud nalezne skript.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-124">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="b5e9b-125">Oprávnění `ControlEvidence` je považováno za velmi výkonné oprávnění, které by mělo být uděleno pouze vysoce důvěryhodnému kódu.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-125">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="b5e9b-126">Chcete-li získat legitimaci ze sestavení, použijte `this.GetType().Assembly.Evidence`.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-126">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="b5e9b-127">K získání legitimace z identifikátoru URI (Uniform Resource Identifier) použijte `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-127">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="b5e9b-128">Použijete-li <xref:System.Xml.Xsl.XslTransform.Load%2A> metody, které přebírají <xref:System.Xml.XmlResolver>, ale ne `Evidence`, je zóna zabezpečení pro sestavení nastavena na úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-128">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="b5e9b-129">Další informace najdete v tématu <xref:System.Security.SecurityZone> a [pojmenované sady oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b5e9b-129">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="b5e9b-130">Funkce mohou být deklarovány v rámci `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-130">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="b5e9b-131">V následující tabulce jsou uvedeny obory názvů, které jsou ve výchozím nastavení podporovány.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-131">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="b5e9b-132">Můžete použít třídy mimo uvedené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-132">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="b5e9b-133">Nicméně tyto třídy musí být plně kvalifikované.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-133">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="b5e9b-134">Výchozí obory názvů</span><span class="sxs-lookup"><span data-stu-id="b5e9b-134">Default Namespaces</span></span>|<span data-ttu-id="b5e9b-135">Popis</span><span class="sxs-lookup"><span data-stu-id="b5e9b-135">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="b5e9b-136">Systém</span><span class="sxs-lookup"><span data-stu-id="b5e9b-136">System</span></span>|<span data-ttu-id="b5e9b-137">Systémová třída</span><span class="sxs-lookup"><span data-stu-id="b5e9b-137">System class.</span></span>|  
|<span data-ttu-id="b5e9b-138">System.Collection</span><span class="sxs-lookup"><span data-stu-id="b5e9b-138">System.Collection</span></span>|<span data-ttu-id="b5e9b-139">Třídy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-139">Collection classes.</span></span>|  
|<span data-ttu-id="b5e9b-140">System.Text</span><span class="sxs-lookup"><span data-stu-id="b5e9b-140">System.Text</span></span>|<span data-ttu-id="b5e9b-141">Třídy textu.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-141">Text classes.</span></span>|  
|<span data-ttu-id="b5e9b-142">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="b5e9b-142">System.Text.RegularExpressions</span></span>|<span data-ttu-id="b5e9b-143">Třídy regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-143">Regular expression classes.</span></span>|  
|<span data-ttu-id="b5e9b-144">System.Xml</span><span class="sxs-lookup"><span data-stu-id="b5e9b-144">System.Xml</span></span>|<span data-ttu-id="b5e9b-145">Základní třídy XML.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-145">Core XML classes.</span></span>|  
|<span data-ttu-id="b5e9b-146">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="b5e9b-146">System.Xml.Xsl</span></span>|<span data-ttu-id="b5e9b-147">Třídy XSLT.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-147">XSLT classes.</span></span>|  
|<span data-ttu-id="b5e9b-148">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="b5e9b-148">System.Xml.XPath</span></span>|<span data-ttu-id="b5e9b-149">Třídy jazyka XML Path (XPath).</span><span class="sxs-lookup"><span data-stu-id="b5e9b-149">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="b5e9b-150">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="b5e9b-150">Microsoft.VisualBasic</span></span>|<span data-ttu-id="b5e9b-151">Třídy pro skripty Microsoft Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-151">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="b5e9b-152">Je-li funkce deklarována, je obsažena v bloku skriptu.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-152">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="b5e9b-153">Šablony stylů mohou obsahovat více bloků skriptu, z nichž každý pracuje nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-153">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="b5e9b-154">To znamená, že pokud provádíte uvnitř bloku skriptu, nemůžete volat funkci, která je definována v jiném bloku skriptu, pokud není deklarována tak, aby měla stejný obor názvů a stejný skriptovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-154">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="b5e9b-155">Vzhledem k tomu, že každý blok skriptu může být ve vlastním jazyce a blok je analyzován podle gramatických pravidel daného jazykového analyzátoru, je nutné použít správnou syntaxi používaného jazyka.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-155">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="b5e9b-156">Například pokud jste v bloku C# skriptu, pak se jedná o chybu při použití uzlu komentáře XML `<!-- an XML comment -->` v bloku.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-156">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="b5e9b-157">Zadané argumenty a návratové hodnoty, které jsou definovány funkcemi skriptu, musí být jedním z typů XPath nebo XSLT typu konsorcium World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="b5e9b-157">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="b5e9b-158">V následující tabulce jsou uvedeny odpovídající typy W3C, ekvivalentní .NET Framework třídy (Type) a zda typ W3C je typ XPath nebo typ XSLT.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-158">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="b5e9b-159">Type</span><span class="sxs-lookup"><span data-stu-id="b5e9b-159">Type</span></span>|<span data-ttu-id="b5e9b-160">Ekvivalentní třída .NET Framework (typ)</span><span class="sxs-lookup"><span data-stu-id="b5e9b-160">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="b5e9b-161">Typ XPath nebo typ XSLT</span><span class="sxs-lookup"><span data-stu-id="b5e9b-161">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="b5e9b-162">String</span><span class="sxs-lookup"><span data-stu-id="b5e9b-162">String</span></span>|<span data-ttu-id="b5e9b-163">System. String</span><span class="sxs-lookup"><span data-stu-id="b5e9b-163">System.String</span></span>|<span data-ttu-id="b5e9b-164">XPath</span><span class="sxs-lookup"><span data-stu-id="b5e9b-164">XPath</span></span>|  
|<span data-ttu-id="b5e9b-165">Boolean</span><span class="sxs-lookup"><span data-stu-id="b5e9b-165">Boolean</span></span>|<span data-ttu-id="b5e9b-166">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="b5e9b-166">System.Boolean</span></span>|<span data-ttu-id="b5e9b-167">XPath</span><span class="sxs-lookup"><span data-stu-id="b5e9b-167">XPath</span></span>|  
|<span data-ttu-id="b5e9b-168">Počet</span><span class="sxs-lookup"><span data-stu-id="b5e9b-168">Number</span></span>|<span data-ttu-id="b5e9b-169">System.Double</span><span class="sxs-lookup"><span data-stu-id="b5e9b-169">System.Double</span></span>|<span data-ttu-id="b5e9b-170">XPath</span><span class="sxs-lookup"><span data-stu-id="b5e9b-170">XPath</span></span>|  
|<span data-ttu-id="b5e9b-171">Fragment stromu výsledků</span><span class="sxs-lookup"><span data-stu-id="b5e9b-171">Result Tree Fragment</span></span>|<span data-ttu-id="b5e9b-172">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b5e9b-172">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="b5e9b-173">XSLT</span><span class="sxs-lookup"><span data-stu-id="b5e9b-173">XSLT</span></span>|  
|<span data-ttu-id="b5e9b-174">Sada uzlů</span><span class="sxs-lookup"><span data-stu-id="b5e9b-174">Node Set</span></span>|<span data-ttu-id="b5e9b-175">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="b5e9b-175">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="b5e9b-176">XPath</span><span class="sxs-lookup"><span data-stu-id="b5e9b-176">XPath</span></span>|  
  
 <span data-ttu-id="b5e9b-177">Pokud funkce skriptu využívá jeden z následujících číselných typů: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single nebo Decimal, jsou nuceni zdvojnásobit, což se mapuje na číslo typu XPath W3C.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-177">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="b5e9b-178">Všechny ostatní typy jsou vynuceny řetězcem voláním metody `ToString`.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-178">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="b5e9b-179">Pokud funkce skriptu využívá jiný typ než ty, které jsou uvedeny výše, nebo pokud funkce není zkompilována, když je šablona stylů načtena do objektu <xref:System.Xml.Xsl.XslTransform>, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-179">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="b5e9b-180">Při použití prvku `msxsl:script` se důrazně doporučuje, aby se skript, bez ohledu na jazyk, umístil do oddílu CDATA.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-180">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="b5e9b-181">Například následující kód XML ukazuje šablonu oddílu CDATA, kde je váš kód umístěn.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-181">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="b5e9b-182">Důrazně doporučujeme, aby se veškerý obsah skriptu umístil do oddílu CDATA, protože operátory, identifikátory nebo oddělovače pro daný jazyk mají potenciál, který je špatně interpretován jako XML.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-182">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="b5e9b-183">Následující příklad ukazuje použití logického operátoru AND ve skriptu.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-183">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="b5e9b-184">Vyvolá výjimku, protože ampersandy nejsou uvozeny řídicími znaky.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-184">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="b5e9b-185">Dokument je načten jako XML a na text mezi značkami `msxsl:script` elementů se neaplikuje žádné speciální zacházení.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-185">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5e9b-186">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5e9b-186">Example</span></span>  
 <span data-ttu-id="b5e9b-187">V následujícím příkladu je použit vložený skript k výpočtu obvodu kružnice s daným poloměrem.</span><span class="sxs-lookup"><span data-stu-id="b5e9b-187">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.               
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
    writer.Close()  
  End Sub   
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main()  
   {  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.               
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }  
}  
```  
  
## <a name="input"></a><span data-ttu-id="b5e9b-188">Vstup</span><span class="sxs-lookup"><span data-stu-id="b5e9b-188">Input</span></span>  
 <span data-ttu-id="b5e9b-189">Number. XML</span><span class="sxs-lookup"><span data-stu-id="b5e9b-189">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>  
```  
  
 <span data-ttu-id="b5e9b-190">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="b5e9b-190">calc.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius)  
     {  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">    
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>   
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="b5e9b-191">Výstup</span><span class="sxs-lookup"><span data-stu-id="b5e9b-191">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5e9b-192">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5e9b-192">See also</span></span>

- [<span data-ttu-id="b5e9b-193">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="b5e9b-193">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
