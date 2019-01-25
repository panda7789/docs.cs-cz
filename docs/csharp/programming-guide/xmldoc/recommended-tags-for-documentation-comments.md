---
title: Doporučené značky pro dokumentační komentáře - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: bdebe26c89f3c7e8d34d34f305d658cd481cd677
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723430"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)
Kompilátor jazyka C# zpracuje komentáře dokumentace ve vašem kódu a je ve formátu XML do souboru, jehož název zadáte **/doc** možnost příkazového řádku. Chcete-li vytvořit finální dokumentaci na základě souboru generovaného kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 Značky jsou zpracovány konstrukcí jako jsou typy a členy typu.  
  
> [!NOTE]
>  Dokumentační komentáře nelze použít pro obor názvů.  
  
 Kompilátor bude zpracovávat všechny značky, který je platný kód XML. Následující značky poskytují funkce obecně používaných v dokumentaci pro uživatele.  
  
## <a name="tags"></a>Značky  
  
||||  
|---|---|---|  
|[\<c>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para>](../../../csharp/programming-guide/xmldoc/para.md)|[\<see>](../../../csharp/programming-guide/xmldoc/see.md)*|  
|[\<code>](../../../csharp/programming-guide/xmldoc/code.md)|[\<Param >](../../../csharp/programming-guide/xmldoc/param.md)*|[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)*|  
|[\<example>](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref>](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<summary>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)*|[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)*|[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)*|  
|[\<include>](../../../csharp/programming-guide/xmldoc/include.md)*|[\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[\<list>](../../../csharp/programming-guide/xmldoc/list.md)|[\<returns>](../../../csharp/programming-guide/xmldoc/returns.md)|[\<value>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 (* označuje, že kompilátor ověří syntaxi.)  
  
 Pokud chcete ostré závorky se zobrazí v textu Dokumentační komentář, použijte `<` a `>`, jak je znázorněno v následujícím příkladu.  
  
```csharp  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [/ DOC (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
