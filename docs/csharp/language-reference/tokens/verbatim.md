---
title: '@ (Referenční dokumentace jazyka C#)'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdf8735894594acab31586e539f90e426db97f24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289175"
---
# <a name="-c-reference"></a>@ (Referenční dokumentace jazyka C#)

`@` Speciální znak slouží jako typu verbatim identifikátor. Dá se následujícími způsoby:

1. Chcete-li povolit klíčová slova jazyka C# má být použit jako identifikátory. `@` Znak předpony element kódu, který kompilátor je interpretovat jako identifikátor, nikoli klíčové slovo C#. Následující příklad používá `@` znak zadat identifikátor s názvem `for` používající v `for` smyčky.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Označuje, že řetězcový literál doslovné interpretovat. `@` Definuje znak v této instanci *typu verbatim řetězcový literál*. Jednoduchý řídicí sekvence (, jako `"\\"` pro zpětné lomítko), šestnáctková řídicí sekvence (, jako `"\x0041"` pro velká A) a Unicode řídicí sekvence (například `"\u0041"` pro velká A) se interpretují oznámena. Uvozovky řídicí sekvence (`""`) neinterpretuje oznámena; vyvolá jednoduché uvozovky. Kromě toho v případě typu verbatim [interpolované řetězce](interpolated.md) složené závorce řídicích sekvencí (`{{` a `}}`) nejsou interpretovat oznámena; vytvářejí jeden závorek znaků. V následujícím příkladu definuje dvě cesty k souborům identické, jeden s použitím regulárních řetězcový literál a dalších pomocí typu verbatim řetězcový literál. Toto je jedna z více běžná použití služby typu verbatim textové literály.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Následující příklad ilustruje účinek definování regulární řetězcový literál a typu verbatim řetězcový literál, které obsahují znak stejné pořadí.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Chcete-li povolit kompilátoru k rozlišení mezi atributy v případě konfliktu názvů. Atribut je typ, který je odvozen od <xref:System.Attribute>. Jeho název typu obvykle zahrnuje přípona **atribut**, i když kompilátor nevynucuje touto konvencí. Atribut může pak odkazovat v kódu buď jeho typ úplný název (například `[InfoAttribute]` nebo jeho zkrácený název (například `[Info]`). Ale ke konfliktu názvů v případě dva zkrátit názvy typů atributů jsou identické, a obsahuje jeden název typu **atribut** příponu ale dalších neexistuje. Například následující kód nepodaří kompilovat, protože kompilátor nemůže určit, zda `Info` nebo `InfoAttribute` je použit atribut `Example` – třída.

   ```csharp
   using System;

   [AttributeUsage(AttributeTargets.Class)]
   public class Info : Attribute
   {
      private string information;
      
      public Info(string info)
      {
          information = info;
      }
   }

   [AttributeUsage(AttributeTargets.Method)]
   public class InfoAttribute : Attribute
   {
      private string information;
      
      public InfoAttribute(string info)
      {
          information = info;
      }
   }

   [Info("A simple executable.")]
   public class Example
   {
      [InfoAttribute("The entry point.")]
      public static void Main()
      {
      }
   }
   ```  

   Pokud typu verbatim identifikátor slouží k identifikaci `Info` atribut v příkladu se zkompiluje úspěšně.

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Speciální znaky v jazyce C#](../../../csharp/language-reference/tokens/index.md)
