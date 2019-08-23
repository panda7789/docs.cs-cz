---
title: Reflexe (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 9b4322d83ad43cd3e49647df49c15bb5c917e1be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924094"
---
# <a name="reflection-c"></a>Reflexe (C#)
Reflexe poskytuje objekty ( <xref:System.Type>typu), které popisují sestavení, moduly a typy. Můžete použít reflexi k dynamickému vytvoření instance typu, svázání typu s existujícím objektem nebo získat typ z existujícího objektu a vyvolat jeho metody nebo získat přístup k jeho polím a vlastnostem. Pokud používáte atributy v kódu, reflexe vám umožní přístup k nim. Další informace najdete v tématu [atributy](../../../standard/attributes/index.md).  
  
 Tady je jednoduchý příklad reflexe pomocí statické metody `GetType` – zděděné všemi typy `Object` ze základní třídy – pro získání typu proměnné:  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 Výstup je:  
  
 `System.Int32`  
  
 Následující příklad používá reflexi k získání úplného názvu načteného sestavení.  
  
```csharp  
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 Výstup je:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
> C# Klíčová `protected` slova `internal` a nemají žádný význam v Il a nejsou použity v rozhraních API reflexe. Odpovídající výrazy v IL jsou *rodina* a *sestavení*. K identifikaci `internal` metody pomocí reflexe <xref:System.Reflection.MethodBase.IsAssembly%2A> použijte vlastnost. K identifikaci `protected internal` metody <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>použijte.  
  
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

- [Průvodce programováním v jazyce C#](../index.md)
- [Sestavení v modulu CLR (Common Language Runtime)](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
