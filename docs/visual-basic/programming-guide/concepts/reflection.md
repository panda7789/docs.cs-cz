---
title: Reflexe (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: d2ad8957d308aa98935c862ec1864b6682be904b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783523"
---
# <a name="reflection-visual-basic"></a>Reflexe (Visual Basic)
Reflexe poskytuje objekty (typu <xref:System.Type>), které popisují sestavení, modulů a typů. Vám pomůže odrazu dynamicky vytvořit instanci typu, navázat na existující objekt, nebo získat typ z existujícího objektu a volat jeho metody nebo přístup k vlastnostem a polím. Pokud používáte atributy ve vašem kódu, reflexe umožňuje přistupovat k nim. Další informace najdete v tématu [atributy](../../../standard/attributes/index.md).  
  
 Tady je jednoduchý příklad použití statické metody reflexe `GetType` – zděděný všechny typy z `Object` základní třídy – získat typ proměnné:  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 Výstup bude:  
  
 `System.Int32`  
  
 Následující příklad používá reflexi získat úplný název načteného sestavení.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 Výstup bude:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>Přehled reflexe  
 Reflexe je užitečná v následujících situacích:  
  
- Pokud máte přístup k atributům v metadatech váš program. Další informace najdete v tématu [načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
- Pro prozkoumání a vytvoření instance typů v sestavení.  
  
- Pro vytváření nových typů v době běhu. Použití tříd v <xref:System.Reflection.Emit>.  
  
- Pro provádění pozdní vazby, přístup k metodám na typy vytvořené v době běhu. Naleznete v tématu [dynamické načtení a použití typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
- [Reflexe](../../../framework/reflection-and-codedom/reflection.md)  
  
- [Zobrazení informací o typu](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [Reflexe a obecné typy](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [Načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce Visual Basic](../../../visual-basic/programming-guide/index.md)
- [Sestavení v modulu CLR (Common Language Runtime)](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
