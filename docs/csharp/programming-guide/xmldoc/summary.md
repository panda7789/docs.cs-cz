---
title: <summary> – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 4a509c002bb6a55b4751712925ae7cc613911af2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587616"
---
# <a name="summary-c-programming-guide"></a>\<souhrnný > (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>Parametry  
 `description`  
 Souhrn objektu.  
  
## <a name="remarks"></a>Poznámky  
 Značka \<> souhrnu by měla být použita k popisu typu nebo člena typu. K přidání doplňujících informací do popisu typu použijte [ \<poznámky >](./remarks.md) . Pomocí [atributu cref](./cref-attribute.md) můžete povolit nástroje dokumentace, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) , a vytvářet interní hypertextové odkazy na stránky dokumentace pro prvky kódu.  
  
 Text pro \<značku Summary > je jediným zdrojem informací o typu v technologii IntelliSense a je také zobrazen v okně Prohlížeč objektů.  
  
 Zkompilujte pomocí [/doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte dokumentační komentáře do souboru. Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
 Předchozí příklad vytvoří následující soubor XML.  
  
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
 Následující příklad ukazuje, jak vytvořit `cref` odkaz na obecný typ.  
  
 [!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]  
  
 Předchozí příklad vytvoří následující soubor XML.  
  
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

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
