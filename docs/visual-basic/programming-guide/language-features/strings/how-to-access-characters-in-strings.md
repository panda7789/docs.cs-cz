---
title: 'Postupy: Přístup ke znakům v řetězcích'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: fa5920cfd25f61f6e6c7d5438ef7c0e38a48fa1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401950"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Postupy: Přístup ke znakům v řetězcích v jazyce Visual Basic
Tento příklad ukazuje, jak použít <xref:System.String.Chars%2A> vlastnost pro přístup k znaku v zadaném umístění v řetězci.  
  
## <a name="example"></a>Příklad  
 Někdy je užitečné mít data o znacích v řetězci a umístění těchto znaků v rámci řetězce. Řetězec můžete představit jako pole znaků ( `Char` instance); můžete načíst konkrétní znak odkazem na index daného znaku prostřednictvím <xref:System.String.Chars%2A> Vlastnosti.  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 `index`Parametr <xref:System.String.Chars%2A> vlastnosti je založený na nule.  
  
## <a name="robust-programming"></a>Robustní programování  
 <xref:System.String.Chars%2A>Vlastnost vrátí znak na zadané pozici. Některé znaky Unicode však mohou být reprezentovány více než jedním znakem. Další informace o tom, jak pracovat se znaky kódování Unicode, naleznete v tématu [How to: Convert String to Array of Characters](how-to-convert-a-string-to-an-array-of-characters.md).  
  
 <xref:System.String.Chars%2A>Vlastnost vyvolá <xref:System.IndexOutOfRangeException> výjimku `index` , pokud je parametr větší nebo roven délce řetězce, nebo pokud je menší než nula.  
  
## <a name="see-also"></a>Viz také

- <xref:System.String.Chars%2A>
- [Postupy: Převod řetězce na pole znaků](how-to-convert-a-string-to-an-array-of-characters.md)
- [Převod mezi řetězci a ostatními datovými typy v jazyce Visual Basic](converting-between-strings-and-other-data-types.md)
- [Řetězce](index.md)
