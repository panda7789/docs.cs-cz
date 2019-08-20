---
title: <see>– C# Průvodce programováním
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
ms.openlocfilehash: e292e116ac468246bfe81e1eb5d5c5819a506701
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587683"
---
# <a name="see-c-programming-guide"></a>\<viz > (C# Průvodce programováním)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor zkontroluje, zda daný prvek kódu existuje a předá `member` do názvu elementu ve výstupním souboru XML. Umístit *člena* v uvozovkách ("").  
  
## <a name="remarks"></a>Poznámky  
 Značka \<Zobrazit > umožňuje zadat odkaz v rámci textu. [ Použijte\<SeeAlso >](./seealso.md) k označení, že text by měl být umístěn v části Viz také. Pomocí [atributu cref](./cref-attribute.md) můžete vytvořit interní hypertextové odkazy na stránky dokumentace pro prvky kódu.  
  
 Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.  
  
 Následující příklad ukazuje \<značku > v části Summary.  
  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
