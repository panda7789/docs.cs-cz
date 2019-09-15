---
title: Reflexe (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 6d1206d84dec4202a7dad8f03c3d88c8a97ff5ba
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972122"
---
# <a name="reflection-visual-basic"></a>Reflexe (Visual Basic)
Reflexe poskytuje objekty ( <xref:System.Type>typu), které popisují sestavení, moduly a typy. Můžete použít reflexi k dynamickému vytvoření instance typu, svázání typu s existujícím objektem nebo získat typ z existujícího objektu a vyvolat jeho metody nebo získat přístup k jeho polím a vlastnostem. Pokud používáte atributy v kódu, reflexe vám umožní přístup k nim. Další informace najdete v tématu [atributy](../../../standard/attributes/index.md).  
  
 Tady je jednoduchý příklad reflexe pomocí statické metody `GetType` – zděděné všemi typy `Object` ze základní třídy – pro získání typu proměnné:  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 Výstup je:  
  
 `System.Int32`  
  
 Následující příklad používá reflexi k získání úplného názvu načteného sestavení.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 Výstup je:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>Přehled reflexe  
 Reflexe je užitečná v následujících situacích:  
  
- Pokud budete mít přístup k atributům v metadatech vašeho programu. Další informace najdete v tématu [načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
- Pro zkoumání a vytváření instancí typů v sestavení.  
  
- Pro vytváření nových typů za běhu. Použijte třídy v <xref:System.Reflection.Emit>.  
  
- Pro provádění pozdní vazby získáte přístup k metodám typů vytvořeným v době běhu. Viz téma [Dynamické načítání a používání typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
- [Reflexe](../../../framework/reflection-and-codedom/reflection.md)  
  
- [Zobrazení informací o typu](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [Reflexe a obecné typy](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [Načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním Visual Basic](../../../visual-basic/programming-guide/index.md)
- [Sestavení v .NET](../../../standard/assembly/index.md)
