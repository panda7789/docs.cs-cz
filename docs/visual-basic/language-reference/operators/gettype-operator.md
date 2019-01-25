---
title: GetType – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: cfb54858286ed31d566b5aeb46faed9070f110bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612837"
---
# <a name="gettype-operator-visual-basic"></a>GetType – operátor (Visual Basic)
Vrátí <xref:System.Type> objekt zadaného typu. <xref:System.Type> Objekt poskytuje informace o typu jako jeho vlastnosti, metody a události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---|---|  
|`typename`|Název typu, pro kterou vyžadujete informace.|  
  
## <a name="remarks"></a>Poznámky  
 `GetType` Operátor vrátí <xref:System.Type> objekt pro zadaný rozbočovač `typename`. Můžete předat název libovolného typu definované v `typename`. Ta zahrnují následující:  
  
-   Zadejte všechna data v jazyce Visual Basic, například `Boolean` nebo `Date`.  
  
-   Všechny třídy rozhraní .NET Framework, struktura, modul nebo rozhraní, jako například <xref:System.ArgumentException?displayProperty=nameWithType> nebo <xref:System.Double?displayProperty=nameWithType>.  
  
-   Všechny třídy, struktury, modul nebo rozhraní definovaných v aplikaci.  
  
-   Jakékoli pole definovaných v aplikaci.  
  
-   Jakýkoli delegát definovaných v aplikaci.  
  
-   Žádné výčtu definované jazyka Visual Basic, rozhraní .NET Framework nebo aplikace.  
  
 Pokud chcete získat objekt typu objektové proměnné, použijte <xref:System.Type.GetType%2A?displayProperty=nameWithType> metody.  
  
 `GetType` Operátor může být užitečná v následujících případech:  
  
-   Třeba získat přístup k metadatům pro typ v době běhu. <xref:System.Type> Objekt poskytuje metadat – například členy typu a informace o nasazení. Je třeba to, například reflexi pro sestavení. Další informace naleznete v tématu <xref:System.Reflection?displayProperty=nameWithType>.  
  
-   Chcete porovnat dva odkazy na objekty a zjistěte, jestli se vztahují na instance stejného typu. V takovém případě `GetType` vrátí odkazy na stejný <xref:System.Type> objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují `GetType` operátor používá.  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
