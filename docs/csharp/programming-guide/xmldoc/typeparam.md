---
title: '&lt;typeparam&gt; (C# Průvodce programováním)'
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 8c7fc1aba05af731d3df80e0b10c2981b5784197
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="lttypeparamgt-c-programming-guide"></a>&lt;typeparam&gt; (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název parametru typu. Uzavřete název do dvojitých uvozovek nahoře ("").  
  
 `description`  
 Popis pro parametr typu.  
  
## <a name="remarks"></a>Poznámky  
 `<typeparam>` Značky by měl být používány komentář pro obecný typ nebo metoda deklaraci k popisu parametr typu. Přidání značky pro každý typ parametr obecného typu nebo metoda.  
  
 Další informace najdete v tématu [obecné typy](../../../csharp/programming-guide/generics/index.md).  
  
 Text pro `<typeparam>` značky se zobrazí v technologii IntelliSense, [okno prohlížeče objekt](http://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) sestava webové komentář kódu.  
  
 Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
