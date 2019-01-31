---
title: <see> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 31806ad06cc97fa27f1944f2500f0f9cbb29f561
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262098"
---
# <a name="see-c-programming-guide"></a>\<Zobrazit > (C# Programming Guide)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje a předá `member` do názvu prvku ve výstupním souboru XML. Místo *člen* do dvojitých uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 \<Naleznete v tématu > značky umožňuje zadat odkaz v rámci textu. Použití [ \<seealso >](../../../csharp/programming-guide/xmldoc/seealso.md) označit, že text by měl být umístěno v části Viz také. Použití [cref – atribut](../../../csharp/programming-guide/xmldoc/cref-attribute.md) k vytvoření interních hypertextových odkazů na stránky dokumentace prvků kódu.  
  
 Kompilovat s [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
 Následující příklad ukazuje \<naleznete v tématu > značky v souhrnné části.  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
