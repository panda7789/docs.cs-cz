---
title: Reflexe (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: fc5c3f6af1a089d824289a55f6781e887b7cfc56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
