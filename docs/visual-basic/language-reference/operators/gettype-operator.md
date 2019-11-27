---
title: GetType – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 4e59bcfaa24c9545ed75c6b5c1d29cad398ac2de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349554"
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
 Operátor `GetType` vrátí objekt <xref:System.Type> pro zadaný `typename`. V `typename`můžete předat název libovolného definovaného typu. Jsou to:  
  
- Libovolný datový typ Visual Basic, například `Boolean` nebo `Date`.  
  
- Jakékoli .NET Framework třídy, struktury, modulu nebo rozhraní, jako je například <xref:System.ArgumentException?displayProperty=nameWithType> nebo <xref:System.Double?displayProperty=nameWithType>.  
  
- Libovolná třída, struktura, modul nebo rozhraní definované vaší aplikací.  
  
- Jakékoli pole definované vaší aplikací.  
  
- Libovolný delegát definovaný vaší aplikací.  
  
- Jakýkoli výčet definovaný Visual Basic, .NET Framework nebo vaší aplikací.  
  
 Chcete-li získat objekt typu proměnné objektu, použijte metodu <xref:System.Type.GetType%2A?displayProperty=nameWithType>.  
  
 Operátor `GetType` může být užitečný v následujících případech:  
  
- Je nutné přístup k metadatům pro typ v době běhu. Objekt <xref:System.Type> poskytuje metadata jako členy typu a informace o nasazení. Potřebujete například, aby odrážely sestavení. Další informace najdete v tématu <xref:System.Reflection?displayProperty=nameWithType>.  
  
- Chcete porovnat dva odkazy na objekty, abyste viděli, zda odkazují na instance stejného typu. Pokud jsou, `GetType` vrátí odkazy na stejný objekt <xref:System.Type>.  
  
## <a name="example"></a>Příklad  
 Následující příklady znázorňují operátor `GetType`, který se používá.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Viz také:

- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
