---
title: '&lt;v tématu&gt; (C# Průvodce programováním)'
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
ms.openlocfilehash: 24fa317a0f89568d9aa1b53849e327ef7615cc7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ltseegt-c-programming-guide"></a>&lt;v tématu&gt; (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor ověří, že element daného kódu existuje a předá `member` k názvu elementu ve výstupu XML. Místní *člen* v rámci dvojitých uvozovek nahoře ("").  
  
## <a name="remarks"></a>Poznámky  
 \<Najdete v části > značka umožňuje zadat odkaz z v textu. Použití [ \<seealso >](../../../csharp/programming-guide/xmldoc/seealso.md) indikující, že text mají být umístěny v části Viz také. Použití [cref – atribut](../../../csharp/programming-guide/xmldoc/cref-attribute.md) k vytvoření interní hypertextové odkazy na stránky dokumentace pro elementy kódu.  
  
 Kompilovat s [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.  
  
 Následující příklad ukazuje \<najdete v části > v části Souhrn značku.  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Doporučené značky pro komentáře dokumentace](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
