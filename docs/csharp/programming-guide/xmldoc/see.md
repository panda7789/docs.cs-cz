---
title: Průvodce C# programováním <see>
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
ms.openlocfilehash: 995b67362bccbc3527f44e5a1d6b659f330e3afd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711711"
---
# <a name="see-c-programming-guide"></a>\<najdete v >C# (Průvodce programováním).
## <a name="syntax"></a>Syntaxe  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor zkontroluje, zda daný prvek kódu existuje a předá `member` k názvu elementu ve výstupním souboru XML. Umístit *člena* v uvozovkách ("").  
  
## <a name="remarks"></a>Poznámky  
 \<Zobrazit značku > umožňuje zadat odkaz v rámci textu. Použijte [\<seealso >](./seealso.md) k označení toho, že text by měl být umístěn v části Viz také. Pomocí [atributu cref](./cref-attribute.md) můžete vytvořit interní hypertextové odkazy na stránky dokumentace pro prvky kódu.  
  
 Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.  
  
 Následující příklad ukazuje \<zobrazení značky > v rámci oddílu Summary.  
  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Doporučené značky pro komentáře dokumentace](./recommended-tags-for-documentation-comments.md)
