---
title: Reflexe
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 43c05a0b3bbfc3dfc304b1aed3f689625a40229a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413177"
---
# <a name="reflection-visual-basic"></a>Reflexe (Visual Basic)
Reflexe poskytuje objekty (typu <xref:System.Type> ), které popisují sestavení, moduly a typy. Můžete použít reflexi k dynamickému vytvoření instance typu, svázání typu s existujícím objektem nebo získat typ z existujícího objektu a vyvolat jeho metody nebo získat přístup k jeho polím a vlastnostem. Pokud používáte atributy v kódu, reflexe vám umožní přístup k nim. Další informace najdete v tématu [atributy](../../../standard/attributes/index.md).  
  
 Tady je jednoduchý příklad reflexe pomocí statické metody `GetType` – zděděné všemi typy ze `Object` základní třídy – pro získání typu proměnné:  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 Výstup bude následující:  
  
 `System.Int32`  
  
 Následující příklad používá reflexi k získání úplného názvu načteného sestavení.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 Výstup bude následující:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>Přehled reflexe  
 Reflexe je užitečná v následujících situacích:  
  
- Pokud budete mít přístup k atributům v metadatech vašeho programu. Další informace najdete v tématu [načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
- Pro zkoumání a vytváření instancí typů v sestavení.  
  
- Pro vytváření nových typů za běhu. Použijte třídy v <xref:System.Reflection.Emit> .  
  
- Pro provádění pozdní vazby získáte přístup k metodám typů vytvořeným v době běhu. Viz téma [Dynamické načítání a používání typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace najdete tady:  
  
- [Reflexe](../../../framework/reflection-and-codedom/reflection.md)  
  
- [Zobrazení informací o typu](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [Reflexe a obecné typy](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [Načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Viz také

- [Příručka k programování v jazyce Visual Basic](../index.md)
- [Sestavení v .NET](../../../standard/assembly/index.md)
