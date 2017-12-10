---
title: Reflexe (C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 68a586fd8a8a8fbe6e351efa3e51c5ba1d2ff4d7
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="reflection-c"></a>Reflexe (C#)
Reflexe poskytuje objekty (typu <xref:System.Type>) popisují sestavení, moduly a typy. Reflexe můžete dynamicky vytvořit instanci typu, typ vazby s existujícím objektem, nebo z existujícího objektu získat typ a volat její metody nebo přístup k jeho polí a vlastností. Pokud používáte atributy ve vašem kódu, reflexe umožňuje přistupovat k nim. Další informace najdete v tématu [atributy](../../../../docs/standard/attributes/index.md).  
  
 Zde je jednoduchý příklad použití statické metody reflexe `GetType` – zděděné z pro všechny typy `Object` základní třída - získat požadovaný typ proměnné:  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 Výstup je:  
  
 `System.Int32`  
  
 Následující příklad používá reflexe získat úplný název načíst sestavení.  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 Výstup je:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  Klíčová slova jazyka C# `protected` a `internal` mít žádný význam v IL a nepoužívají se v rozhraní API reflexe. Odpovídající podmínky v IL *rodiny* a *sestavení*. K identifikaci `internal` metoda pomocí reflexe, použijte <xref:System.Reflection.MethodBase.IsAssembly%2A> vlastnost. K identifikaci `protected internal` metoda, použijte <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.  
  
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Sestavení v modulu Common Language Runtime](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
