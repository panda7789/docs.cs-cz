---
title: Reflexe (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4593aeef13f5d1d0c223b40e266556cb2bcfee5f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595553"
---
# <a name="reflection-c"></a>Reflexe (C#)
Reflexe poskytuje objekty (typu <xref:System.Type>), které popisují sestavení, modulů a typů. Vám pomůže odrazu dynamicky vytvořit instanci typu, navázat na existující objekt, nebo získat typ z existujícího objektu a volat jeho metody nebo přístup k vlastnostem a polím. Pokud používáte atributy ve vašem kódu, reflexe umožňuje přistupovat k nim. Další informace najdete v tématu [atributy](../../../../docs/standard/attributes/index.md).  
  
 Tady je jednoduchý příklad použití statické metody reflexe `GetType` – zděděný všechny typy z `Object` základní třídy – získat typ proměnné:  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 Výstup bude:  
  
 `System.Int32`  
  
 Následující příklad používá reflexi získat úplný název načteného sestavení.  
  
```csharp  
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 Výstup bude:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  Klíčová slova jazyka C# `protected` a `internal` nemají význam IL a nepoužívají se v rozhraní API reflexe. Odpovídající výrazy v IL jsou *řady* a *sestavení*. K identifikaci `internal` pomocí reflexe, použijte metodu <xref:System.Reflection.MethodBase.IsAssembly%2A> vlastnost. K identifikaci `protected internal` metody, použijte <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.  
  
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

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Sestavení v modulu CLR (Common Language Runtime)](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
