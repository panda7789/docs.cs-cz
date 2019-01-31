---
title: <summary> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: c4f05e80fff386a5b0628c01605784c32d7ddaf5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261309"
---
# <a name="summary-c-programming-guide"></a>\<Souhrn > (C# Programming Guide)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Přehled objektu.  
  
## <a name="remarks"></a>Poznámky  
 \<Summary > Značka by měla sloužit k popisu typu nebo člena typu. Použití [ \<remarks >](../../../csharp/programming-guide/xmldoc/remarks.md) přidat doplňující informace pro popis typu. Použití [cref – atribut](../../../csharp/programming-guide/xmldoc/cref-attribute.md) umožňující dokumentace nástroje [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) k vytvoření interních hypertextových odkazů na stránky dokumentace prvků kódu.  
  
 Text \<summary > značky je jediný zdroj informací o typu v IntelliSense a také se zobrazí v okně prohlížeče objektů.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru. Chcete-li vytvořit finální dokumentaci na základě souboru generovaného kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_1.cs)]  
  
 Předchozí příklad vytváří následující soubor XML.  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `cref` odkaz na obecném typu.  
  
 [!code-csharp[csProgGuideDocComments#11](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_2.cs)]  
  
 Předchozí příklad vytváří následující soubor XML.  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
