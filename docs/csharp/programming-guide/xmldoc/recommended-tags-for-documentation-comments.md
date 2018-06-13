---
title: Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 54047746db672efbf626eb2d3fc301b341cc49f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338475"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)
Kompilátor jazyka C# zpracovává dokumentační komentáře v kódu a je ve formátu XML v souboru s názvem zadáte v **/doc** možnost příkazového řádku. K vytvoření konečné dokumentaci založenou na soubor generované kompilátorem, můžete vytvořit vlastní nástroj nebo pomocí nástroje, jako například [aplikaci Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 Značky jsou zpracovávány na kód konstruktory, jako jsou typy a členy typu.  
  
> [!NOTE]
>  Dokumentační komentáře nelze použít pro obor názvů.  
  
 Kompilátor zpracuje všechny značky, který je platný kód XML. Následující značky poskytují funkce obvykle používané v dokumentaci pro uživatele.  
  
## <a name="tags"></a>Značky  
  
||||  
|---|---|---|  
|[\<c >](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para >](../../../csharp/programming-guide/xmldoc/para.md)|[\<v tématu >](../../../csharp/programming-guide/xmldoc/see.md)*|  
|[\<kód >](../../../csharp/programming-guide/xmldoc/code.md)|[\<Param >](../../../csharp/programming-guide/xmldoc/param.md)*|[\<Viz také >](../../../csharp/programming-guide/xmldoc/seealso.md)*|  
|[\<Příklad >](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref >](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<Souhrn >](../../../csharp/programming-guide/xmldoc/summary.md)|  
|[\<Výjimka >](../../../csharp/programming-guide/xmldoc/exception.md)*|[\<oprávnění >](../../../csharp/programming-guide/xmldoc/permission.md)*|[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)*|  
|[\<Zahrnout >](../../../csharp/programming-guide/xmldoc/include.md)*|[\<Poznámky >](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[\<Seznam >](../../../csharp/programming-guide/xmldoc/list.md)|[\<Vrátí >](../../../csharp/programming-guide/xmldoc/returns.md)|[\<Hodnota >](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 (* označuje, že kompilátor ověří syntaxi.)  
  
 Pokud chcete lomené závorky, než se objeví v text komentáře dokumentace, použijte `<` a `>`, jak je znázorněno v následujícím příkladu.  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [/ DOC (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
