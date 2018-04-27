---
title: Pomocí skriptování šablony stylů XSLT &lt;msxsl:script&gt;
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
caps.latest.revision: 4
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 01d4271eb5795e3760d289842bdfbdfa11c883fd
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="xslt-stylesheet-scripting-using-ltmsxslscriptgt"></a><span data-ttu-id="8d5be-102">Pomocí skriptování šablony stylů XSLT &lt;msxsl:script&gt;</span><span class="sxs-lookup"><span data-stu-id="8d5be-102">XSLT Stylesheet Scripting Using &lt;msxsl:script&gt;</span></span>
<span data-ttu-id="8d5be-103"><xref:System.Xml.Xsl.XslTransform> Třída podporuje použití vloženého skriptu `script` elementu.</span><span class="sxs-lookup"><span data-stu-id="8d5be-103">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d5be-104"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d5be-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="8d5be-105">Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="8d5be-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="8d5be-106">V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="8d5be-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="8d5be-107"><xref:System.Xml.Xsl.XslTransform> Třída podporuje použití vloženého skriptu `script` elementu.</span><span class="sxs-lookup"><span data-stu-id="8d5be-107">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="8d5be-108">Při načítání šablony stylů žádné definované funkce jsou kompilovaná do převodního jazyka Microsoft (MSIL) je uzavřen do definice třídy a v důsledku mít nedošlo ke ztrátě výkonu.</span><span class="sxs-lookup"><span data-stu-id="8d5be-108">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="8d5be-109">`<msxsl:script>` Element je definován pod:</span><span class="sxs-lookup"><span data-stu-id="8d5be-109">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="8d5be-110">kde `msxsl` je vázán předponu pro obor názvů `urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="8d5be-110">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="8d5be-111">`language` Atribut není povinné, ale -li zadána, jeho hodnota musí být jeden z následujících: C#, VB, JScript, JavaScript, VisualBasic nebo CSharp.</span><span class="sxs-lookup"><span data-stu-id="8d5be-111">The `language` attribute is not mandatory, but if specified, its value must be one of the following: C#, VB, JScript, JavaScript, VisualBasic, or CSharp.</span></span> <span data-ttu-id="8d5be-112">Pokud není zadáno, výchozí jazyk JScript.</span><span class="sxs-lookup"><span data-stu-id="8d5be-112">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="8d5be-113">`language-name` Není malá a velká písmena, proto odpovídají 'JavaScript' a "javascript".</span><span class="sxs-lookup"><span data-stu-id="8d5be-113">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="8d5be-114">`implements-prefix` Atribut je povinný.</span><span class="sxs-lookup"><span data-stu-id="8d5be-114">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="8d5be-115">Tento atribut slouží k deklarace oboru názvů a přidružte ji k blok skriptu.</span><span class="sxs-lookup"><span data-stu-id="8d5be-115">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="8d5be-116">Hodnota tohoto atributu je předpona, která představuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8d5be-116">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="8d5be-117">Tento obor názvů, může být definováno někde v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="8d5be-117">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="8d5be-118">Protože `msxsl:script` element patří do oboru názvů `urn:schemas-microsoft-com:xslt`, šablony stylů musí obsahovat deklaraci oboru názvů `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="8d5be-118">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="8d5be-119">Pokud má volající skriptu nemá <xref:System.Security.Permissions.SecurityPermissionFlag> oprávnění, pak bude nikdy kompilovat skript v šabloně stylů a volání <xref:System.Xml.Xsl.XslTransform.Load%2A> se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="8d5be-119">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="8d5be-120">Pokud má volající `UnmanagedCode` zkompiluje skript oprávnění, ale jsou závislé na důkaz, která se dodává v okamžiku načtení operace, které jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="8d5be-120">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="8d5be-121">Pokud použijete jednu z <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, které berou <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XPath.XPathNavigator> načtení šablony stylů, budete muset použít <xref:System.Xml.Xsl.XslTransform.Load%2A> přetížení, které přijímá <xref:System.Security.Policy.Evidence> parametrů jako jedna z jeho argumenty.</span><span class="sxs-lookup"><span data-stu-id="8d5be-121">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="8d5be-122">Pro prokázání, volající musí mít <xref:System.Security.Permissions.SecurityPermissionFlag> oprávnění k poskytování `Evidence` pro sestavení skriptu.</span><span class="sxs-lookup"><span data-stu-id="8d5be-122">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="8d5be-123">Pokud má volající nemá toto oprávnění, pak se můžete nastavit `Evidence` parametru `null`.</span><span class="sxs-lookup"><span data-stu-id="8d5be-123">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="8d5be-124">To způsobí, že <xref:System.Xml.Xsl.XslTransform.Load%2A> funkce, která se nezdaří, pokud najde skriptu.</span><span class="sxs-lookup"><span data-stu-id="8d5be-124">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="8d5be-125">`ControlEvidence` Oprávnění je považován za velmi výkonné oprávnění, které by měl lze udělit pouze vysoce důvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="8d5be-125">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="8d5be-126">Důkaz z vaší sestavení, použijte `this.GetType().Assembly.Evidence`.</span><span class="sxs-lookup"><span data-stu-id="8d5be-126">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="8d5be-127">Důkaz z identifikátor URI (Uniform Resource), použijte `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span><span class="sxs-lookup"><span data-stu-id="8d5be-127">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="8d5be-128">Pokud používáte <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, které berou <xref:System.Xml.XmlResolver> , ale žádné `Evidence`, výchozí nastavení zóny zabezpečení pro sestavení úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="8d5be-128">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="8d5be-129">Další informace najdete v tématu <xref:System.Security.SecurityZone> a [pojmenované sady oprávnění](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="8d5be-129">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="8d5be-130">Funkce můžete deklarované v rámci `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="8d5be-130">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="8d5be-131">V následující tabulce jsou obory názvů, které jsou podporovány ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="8d5be-131">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="8d5be-132">Můžete třídy mimo uvedené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="8d5be-132">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="8d5be-133">Tyto třídy však musí být úplná.</span><span class="sxs-lookup"><span data-stu-id="8d5be-133">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="8d5be-134">Výchozí obory názvů</span><span class="sxs-lookup"><span data-stu-id="8d5be-134">Default Namespaces</span></span>|<span data-ttu-id="8d5be-135">Popis</span><span class="sxs-lookup"><span data-stu-id="8d5be-135">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="8d5be-136">Systém</span><span class="sxs-lookup"><span data-stu-id="8d5be-136">System</span></span>|<span data-ttu-id="8d5be-137">Třída systému.</span><span class="sxs-lookup"><span data-stu-id="8d5be-137">System class.</span></span>|  
|<span data-ttu-id="8d5be-138">System.Collection</span><span class="sxs-lookup"><span data-stu-id="8d5be-138">System.Collection</span></span>|<span data-ttu-id="8d5be-139">Třídy kolekce.</span><span class="sxs-lookup"><span data-stu-id="8d5be-139">Collection classes.</span></span>|  
|<span data-ttu-id="8d5be-140">System.Text</span><span class="sxs-lookup"><span data-stu-id="8d5be-140">System.Text</span></span>|<span data-ttu-id="8d5be-141">Text třídy.</span><span class="sxs-lookup"><span data-stu-id="8d5be-141">Text classes.</span></span>|  
|<span data-ttu-id="8d5be-142">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="8d5be-142">System.Text.RegularExpressions</span></span>|<span data-ttu-id="8d5be-143">Třídy regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="8d5be-143">Regular expression classes.</span></span>|  
|<span data-ttu-id="8d5be-144">System.Xml</span><span class="sxs-lookup"><span data-stu-id="8d5be-144">System.Xml</span></span>|<span data-ttu-id="8d5be-145">Základní třídy XML.</span><span class="sxs-lookup"><span data-stu-id="8d5be-145">Core XML classes.</span></span>|  
|<span data-ttu-id="8d5be-146">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="8d5be-146">System.Xml.Xsl</span></span>|<span data-ttu-id="8d5be-147">Třídy XSLT.</span><span class="sxs-lookup"><span data-stu-id="8d5be-147">XSLT classes.</span></span>|  
|<span data-ttu-id="8d5be-148">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="8d5be-148">System.Xml.XPath</span></span>|<span data-ttu-id="8d5be-149">Třídy XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="8d5be-149">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="8d5be-150">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="8d5be-150">Microsoft.VisualBasic</span></span>|<span data-ttu-id="8d5be-151">Třídy pro skripty jazyka Microsoft Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8d5be-151">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="8d5be-152">Pokud je deklarovaná funkci, je obsažený v bloku skriptu.</span><span class="sxs-lookup"><span data-stu-id="8d5be-152">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="8d5be-153">Šablony stylů může obsahovat více skriptu bloků, každý operační nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="8d5be-153">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="8d5be-154">To znamená, že pokud spouštění uvnitř bloku skriptu nelze volat funkci, která jste definovali v jiného bloku skriptu, pokud je deklarovaná do mají stejný obor názvů a stejný skriptovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="8d5be-154">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="8d5be-155">Protože každý blok skriptu může být v jeho vlastní jazyk a bloku je analyzována podle pravidel gramatika objektů tohoto analyzátoru jazyka, musíte použít správnou syntaxi pro jazyk používán.</span><span class="sxs-lookup"><span data-stu-id="8d5be-155">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="8d5be-156">Například pokud jste v bloku skriptu jazyka C#, je použít uzel komentáře XML k chybě `<!-- an XML comment -->` v bloku.</span><span class="sxs-lookup"><span data-stu-id="8d5be-156">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="8d5be-157">Zadané argumenty a návratové hodnoty definované funkce skriptu musí být jeden z typů XPath World Wide Web Consortium (W3C) nebo XSLT.</span><span class="sxs-lookup"><span data-stu-id="8d5be-157">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="8d5be-158">Následující tabulka uvádí odpovídající typy W3C ekvivalent rozhraní .NET Framework třídy (typ) a zda typ W3C je XPath typ nebo typ XSLT.</span><span class="sxs-lookup"><span data-stu-id="8d5be-158">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="8d5be-159">Typ</span><span class="sxs-lookup"><span data-stu-id="8d5be-159">Type</span></span>|<span data-ttu-id="8d5be-160">Ekvivalent rozhraní .NET Framework třídy (typ)</span><span class="sxs-lookup"><span data-stu-id="8d5be-160">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="8d5be-161">Výraz XPath typ nebo typ XSLT</span><span class="sxs-lookup"><span data-stu-id="8d5be-161">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="8d5be-162">String</span><span class="sxs-lookup"><span data-stu-id="8d5be-162">String</span></span>|<span data-ttu-id="8d5be-163">System.String</span><span class="sxs-lookup"><span data-stu-id="8d5be-163">System.String</span></span>|<span data-ttu-id="8d5be-164">XPath</span><span class="sxs-lookup"><span data-stu-id="8d5be-164">XPath</span></span>|  
|<span data-ttu-id="8d5be-165">Boolean</span><span class="sxs-lookup"><span data-stu-id="8d5be-165">Boolean</span></span>|<span data-ttu-id="8d5be-166">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="8d5be-166">System.Boolean</span></span>|<span data-ttu-id="8d5be-167">XPath</span><span class="sxs-lookup"><span data-stu-id="8d5be-167">XPath</span></span>|  
|<span data-ttu-id="8d5be-168">Číslo</span><span class="sxs-lookup"><span data-stu-id="8d5be-168">Number</span></span>|<span data-ttu-id="8d5be-169">System.Double</span><span class="sxs-lookup"><span data-stu-id="8d5be-169">System.Double</span></span>|<span data-ttu-id="8d5be-170">XPath</span><span class="sxs-lookup"><span data-stu-id="8d5be-170">XPath</span></span>|  
|<span data-ttu-id="8d5be-171">Fragment výsledek stromu</span><span class="sxs-lookup"><span data-stu-id="8d5be-171">Result Tree Fragment</span></span>|<span data-ttu-id="8d5be-172">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="8d5be-172">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="8d5be-173">XSLT</span><span class="sxs-lookup"><span data-stu-id="8d5be-173">XSLT</span></span>|  
|<span data-ttu-id="8d5be-174">Sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="8d5be-174">Node Set</span></span>|<span data-ttu-id="8d5be-175">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="8d5be-175">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="8d5be-176">XPath</span><span class="sxs-lookup"><span data-stu-id="8d5be-176">XPath</span></span>|  
  
 <span data-ttu-id="8d5be-177">Pokud funkci skript využívá jednu z následujících číselnými typy: Int16, UInt16, Int32, UInt32, Int64, UInt64, jedním nebo Decimal, že jsou nuceno dvakrát, která se mapuje na typ Číslo W3C XPath.</span><span class="sxs-lookup"><span data-stu-id="8d5be-177">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="8d5be-178">Všechny ostatní typy jsou nuceno řetězec voláním `ToString` metoda.</span><span class="sxs-lookup"><span data-stu-id="8d5be-178">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="8d5be-179">Pokud funkci skript využívá typu než výše uvedené, nebo pokud funkce nekompiluje se při načtení šablony stylů do <xref:System.Xml.Xsl.XslTransform> objekt, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8d5be-179">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="8d5be-180">Při použití `msxsl:script` elementu, důrazně doporučujeme, aby na skript, bez ohledu na jazyk, být umístěna uvnitř oddílu CDATA.</span><span class="sxs-lookup"><span data-stu-id="8d5be-180">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="8d5be-181">Například následující kód XML ukazuje šablonu oddílu CDATA, kde je umístěn vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="8d5be-181">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="8d5be-182">Důrazně doporučujeme, aby veškerý obsah skriptu umístit do oddílu CDATA, protože operátory, identifikátory nebo oddělovače pro daný jazyk mohou být právě k nesprávné interpretaci jako XML.</span><span class="sxs-lookup"><span data-stu-id="8d5be-182">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="8d5be-183">Následující příklad ukazuje použití logický operátor AND ve skriptu.</span><span class="sxs-lookup"><span data-stu-id="8d5be-183">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp>  
    public string book(string abc, string xyz)  
    {  if ((abc== abc)&&(abc== xyz)) return bar+xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="8d5be-184">To vyvolá výjimku, protože nejsou uvozené ampersandy.</span><span class="sxs-lookup"><span data-stu-id="8d5be-184">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="8d5be-185">Načte se dokument ve formátu XML a žádné zvláštní zacházení se použije pro text mezi `msxsl:script` značky elementu.</span><span class="sxs-lookup"><span data-stu-id="8d5be-185">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d5be-186">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d5be-186">Example</span></span>  
 <span data-ttu-id="8d5be-187">Následující příklad používá k výpočtu obvodu kruhu zadané jeho radius vloženého skriptu.</span><span class="sxs-lookup"><span data-stu-id="8d5be-187">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
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
  
   public static void Main() {  
  
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
  
## <a name="input"></a><span data-ttu-id="8d5be-188">Vstup</span><span class="sxs-lookup"><span data-stu-id="8d5be-188">Input</span></span>  
 <span data-ttu-id="8d5be-189">Number.XML</span><span class="sxs-lookup"><span data-stu-id="8d5be-189">number.xml</span></span>  
  
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
  
 <span data-ttu-id="8d5be-190">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="8d5be-190">calc.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius){  
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
  
## <a name="output"></a><span data-ttu-id="8d5be-191">Výstup</span><span class="sxs-lookup"><span data-stu-id="8d5be-191">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d5be-192">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d5be-192">See Also</span></span>  
 [<span data-ttu-id="8d5be-193">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="8d5be-193">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
