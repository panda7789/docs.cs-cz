---
title: Reflexe (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b7b94e25d2ca9563cd50f454c94092f18e295863
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="reflection-visual-basic"></a>Reflexe (Visual Basic)
Reflexe poskytuje objekty (typu <xref:System.Type>) popisují sestavení, moduly a typy. Reflexe můžete dynamicky vytvořit instanci typu, typ vazby s existujícím objektem, nebo z existujícího objektu získat typ a volat její metody nebo přístup k jeho polí a vlastností. Pokud používáte atributy ve vašem kódu, reflexe umožňuje přistupovat k nim. Další informace najdete v tématu [atributy](https://msdn.microsoft.com/library/5x6cd29c).  
  
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
 [Sestavení v modulu Common Language Runtime](https://msdn.microsoft.com/library/k3677y81)
