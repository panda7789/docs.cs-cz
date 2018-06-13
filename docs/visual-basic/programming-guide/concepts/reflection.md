---
title: Reflexe (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: f47f78ff9989fc44ad46b66a447061c3fa84a86e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646674"
---
# <a name="reflection-visual-basic"></a>Reflexe (Visual Basic)
Reflexe poskytuje objekty (typu <xref:System.Type>) popisují sestavení, moduly a typy. Reflexe můžete dynamicky vytvořit instanci typu, typ vazby s existujícím objektem, nebo z existujícího objektu získat typ a volat její metody nebo přístup k jeho polí a vlastností. Pokud používáte atributy ve vašem kódu, reflexe umožňuje přistupovat k nim. Další informace najdete v tématu [atributy](../../../standard/attributes/index.md).  
  
 Zde je jednoduchý příklad použití statické metody reflexe `GetType` – zděděné z pro všechny typy `Object` základní třída - získat požadovaný typ proměnné:  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 Výstup je:  
  
 `System.Int32`  
  
 Následující příklad používá reflexe získat úplný název načíst sestavení.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 Výstup je:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>Přehled reflexe  
 Reflexe je užitečné v následujících situacích:  
  
-   Pokud máte přístup k atributům v metadatech vašeho programu. Další informace najdete v tématu [načítání informace uložené v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
-   Pro zkoumání a vytváření instancí typy v sestavení.  
  
-   Pro vytváření nových typů za běhu. Použití třídy v <xref:System.Reflection.Emit>.  
  
-   K provedení pozdní vazba, přístup k metody pro typy vytvořené v době běhu. Podívejte se na téma [dynamické načtení a použití typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
-   [Reflexe](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [Zobrazení informací o typu](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [Reflexe a obecné typy](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [Načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce Visual Basic](../../../visual-basic/programming-guide/index.md)  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
