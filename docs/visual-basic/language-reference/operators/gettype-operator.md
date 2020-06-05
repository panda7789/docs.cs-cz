---
title: GetType – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 37644a9c37ffde084120c5f1e1ee8c87a04ffc3c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371152"
---
# <a name="gettype-operator-visual-basic"></a>GetType – operátor (Visual Basic)
Vrátí <xref:System.Type> objekt pro zadaný typ. <xref:System.Type>Objekt poskytuje informace o typu, jako jsou vlastnosti, metody a události.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---|---|  
|`typename`|Název typu, pro který si přejete získat informace.|  
  
## <a name="remarks"></a>Poznámky  
 `GetType`Operátor vrátí <xref:System.Type> objekt pro zadanou hodnotu `typename` . Můžete předat název libovolného definovaného typu v `typename` . Ta zahrnují následující:  
  
- Libovolný datový typ Visual Basic, například `Boolean` nebo `Date` .  
  
- Jakékoli .NET Framework třídy, struktury, modulu nebo rozhraní, například <xref:System.ArgumentException?displayProperty=nameWithType> nebo <xref:System.Double?displayProperty=nameWithType> .  
  
- Libovolná třída, struktura, modul nebo rozhraní definované vaší aplikací.  
  
- Jakékoli pole definované vaší aplikací.  
  
- Libovolný delegát definovaný vaší aplikací.  
  
- Jakýkoli výčet definovaný Visual Basic, .NET Framework nebo vaší aplikací.  
  
 Pokud chcete získat objekt typu proměnné objektu, použijte <xref:System.Type.GetType%2A?displayProperty=nameWithType> metodu.  
  
 `GetType`Operátor může být užitečný v následujících případech:  
  
- Je nutné přístup k metadatům pro typ v době běhu. <xref:System.Type>Objekt poskytuje metadata jako členy typu a informace o nasazení. Potřebujete například, aby odrážely sestavení. Další informace naleznete v tématu <xref:System.Reflection?displayProperty=nameWithType>.  
  
- Chcete porovnat dva odkazy na objekty, abyste viděli, zda odkazují na instance stejného typu. Pokud jsou, `GetType` vrátí odkazy na stejný <xref:System.Type> objekt.  
  
## <a name="example"></a>Příklad  
 Následující příklady znázorňují operátor, který se `GetType` používá.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Viz také

- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Operátory a výrazy](../../programming-guide/language-features/operators-and-expressions/index.md)
