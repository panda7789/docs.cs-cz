---
title: Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: ef7ba44c0c3a8c660df9627361eb1cabdd9098a0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741943"
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
|[\<c >](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para >](../../../csharp/programming-guide/xmldoc/para.md)|[\<Zobrazit >](../../../csharp/programming-guide/xmldoc/see.md)*|  
|[\<kód >](../../../csharp/programming-guide/xmldoc/code.md)|[\<Param >](../../../csharp/programming-guide/xmldoc/param.md)*|[\<SeeAlso >](../../../csharp/programming-guide/xmldoc/seealso.md)*|  
|[\<Příklad >](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref >](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<Summary >](../../../csharp/programming-guide/xmldoc/summary.md)|  
|[\<výjimky >](../../../csharp/programming-guide/xmldoc/exception.md)*|[\<oprávnění >](../../../csharp/programming-guide/xmldoc/permission.md)*|[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)*|  
|[\<Zahrnout >](../../../csharp/programming-guide/xmldoc/include.md)*|[\<REMARKS >](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[\<Seznam >](../../../csharp/programming-guide/xmldoc/list.md)|[\<Vrátí >](../../../csharp/programming-guide/xmldoc/returns.md)|[\<Hodnota >](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 (* označuje, že kompilátor ověří syntaxi.)  
  
 Pokud chcete ostré závorky se zobrazí v textu Dokumentační komentář, použijte `<` a `>`, jak je znázorněno v následujícím příkladu.  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [/ DOC (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
- [Dokumentační komentáře XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
