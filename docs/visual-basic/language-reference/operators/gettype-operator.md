---
title: GetType – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 2e3e05973f2ef72fef5e429bc98cc58b4b21f2c2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592155"
---
# <a name="gettype-operator-visual-basic"></a>GetType – operátor (Visual Basic)
Vrátí objekt <xref:System.Type> pro zadaný typ. Objekt <xref:System.Type> poskytuje informace o typu, jako jsou vlastnosti, metody a události.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---|---|  
|`typename`|Název typu, pro který si přejete získat informace.|  
  
## <a name="remarks"></a>Poznámky  
 Operátor `GetType` vrátí objekt <xref:System.Type> pro zadaný `typename`. Název libovolného definovaného typu můžete předat `typename`. Ta zahrnují následující:  
  
- Libovolný datový typ Visual Basic, například `Boolean` nebo `Date`.  
  
- Jakékoli .NET Framework třídy, struktury, modulu nebo rozhraní, například <xref:System.ArgumentException?displayProperty=nameWithType> nebo <xref:System.Double?displayProperty=nameWithType>.  
  
- Libovolná třída, struktura, modul nebo rozhraní definované vaší aplikací.  
  
- Jakékoli pole definované vaší aplikací.  
  
- Libovolný delegát definovaný vaší aplikací.  
  
- Jakýkoli výčet definovaný Visual Basic, .NET Framework nebo vaší aplikací.  
  
 Pokud chcete získat objekt typu proměnné objektu, použijte metodu <xref:System.Type.GetType%2A?displayProperty=nameWithType>.  
  
 Operátor `GetType` může být užitečný v následujících případech:  
  
- Je nutné přístup k metadatům pro typ v době běhu. Objekt <xref:System.Type> poskytuje metadata jako členy typu a informace o nasazení. Potřebujete například, aby odrážely sestavení. Další informace naleznete v tématu <xref:System.Reflection?displayProperty=nameWithType>.  
  
- Chcete porovnat dva odkazy na objekty, abyste viděli, zda odkazují na instance stejného typu. Pokud tomu tak je, `GetType` vrátí odkazy na stejný objekt <xref:System.Type>.  
  
## <a name="example"></a>Příklad  
 Následující příklady znázorňují operátor `GetType`, který se používá.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Viz také:

- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
