---
title: "Dynamické načtení a použití typů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- late binding, about late binding
- early binding
- dynamically loading and using types
- implicit late binding
- reflection, dynamically using types
ms.assetid: db985bec-5942-40ec-b13a-771ae98623dc
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b924f1c1b46eb132070b6d582cf065f38a8a600
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="dynamically-loading-and-using-types"></a>Dynamické načtení a použití typů
Reflexe poskytuje infrastrukturu, jako používá kompilátory jazyka [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] a JScript implementovat implicitní pozdní vazba. Vazba je proces vyhledávání deklarace (tedy implementace), která odpovídá jednoznačně zadaného typu. Pokud k tomuto procesu dochází za běhu, spíše než v době kompilace, nazývá pozdní vazba. [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]umožňuje používat implicitní pozdní vazba v kódu; Visual Basic – kompilátor volá metodu helper, která používá reflexe získat typ objektu. Argumenty předávané Pomocná metoda způsobit odpovídající metodu, která má být volána v době běhu. Tyto argumenty jsou instance (objekt), na kterém má být vyvolána metoda, název vyvolaná metoda (string) a argumenty předávané vyvolaná metoda (pole objektů).  
  
 V následujícím příkladu nastavení kompilátoru jazyka Visual Basic používá reflexe implicitně k volání metody na objekt, jehož typ není známý v době kompilace. A **HelloWorld** třída má **PrintHello** metoda, která vytiskne "Hello, World" zřetězen s nějaký text, který je předán **PrintHello** metoda. **PrintHello** metodu s názvem v tomto příkladu je ve skutečnosti <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>; umožňuje kód jazyka Visual Basic **PrintHello** metoda má být volána, jako kdyby byly v kompilaci známý typ objektu (helloObj) čas (časná vazba) a nikoli na běh (pozdní vazba).  
  
```  
Imports System  
Module Hello  
    Sub Main()  
        ' Sets up the variable.  
        Dim helloObj As Object  
        ' Creates the object.  
        helloObj = new HelloWorld()  
        ' Invokes the print method as if it was early bound  
        ' even though it is really late bound.  
        helloObj.PrintHello("Visual Basic Late Bound")  
    End Sub  
End Module  
```  
  
## <a name="custom-binding"></a>Vlastní vazba  
 Kromě používán implicitně kompilátory pro pozdní vazbu, reflexe umožňuje explicitně v kódu provést pozdní vazba.  
  
 [Modul common language runtime](../../../docs/standard/clr.md) podporuje více programovacích jazyků a vazbu pravidla z těchto jazyků lišit. V případě časné vazby generátory kódu zcela řídit tuto vazbu. Pozdní vazba prostřednictvím reflexe, je třeba kontrolovat vazby ve vlastní vazby. <xref:System.Reflection.Binder> Třída poskytuje vlastní ovládací prvek člena výběr a volání.  
  
 Vlastní vazby můžete načíst sestavení za běhu, že sestavení, zadejte typ, který chcete a pak vyvolání metody nebo vlastnosti daný typ nebo pole přístup získat informace o typech. Tato metoda je užitečná, pokud neznáte typ objektu při kompilaci, například pokud je typ objektu závislý na vstup uživatele.  
  
 Následující příklad ukazuje jednoduchý vlastní vazač poskytující žádný argument typu převod. Kód `Simple_Type.dll` předchází hlavní příklad. Ujistěte se, k vytvoření `Simple_Type.dll` a poté zahrnout odkaz na projekt v čase vytvoření buildu.  
  
 [!code-cpp[Conceptual.Types.Dynamic#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.Dynamic#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.Dynamic#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source1.vb#1)]  
  
### <a name="invokemember-and-createinstance"></a>Metodu InvokeMember a CreateInstance –  
 Použití <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType> k vyvolání člena typu. **CreateInstance** různé metody třídy, jako například <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> a <xref:System.Reflection.Assembly.CreateInstance%2A?displayProperty=nameWithType>, jsou specializované formy **metodu InvokeMember** , vytvoření nové instance zadaného typu. **Vazač** třída se používá pro překlad IP adres a argument převod přetížení v těchto metod.  
  
 Následující příklad ukazuje tři možné kombinace argument převod (převod typu) a výběr členů. V případě 1 je potřeba žádný argument převod nebo člen výběr. V případě 2 je potřeba jenom výběr členů. V případě 3 je potřeba pouze argument převod.  
  
 [!code-cpp[Conceptual.Types.Dynamic#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.Dynamic#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.Dynamic#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source2.vb#2)]  
  
 Řešení přetížení je potřeba, pokud je k dispozici více než jednoho člena se stejným názvem. <xref:System.Reflection.Binder.BindToMethod%2A?displayProperty=nameWithType> a <xref:System.Reflection.Binder.BindToField%2A?displayProperty=nameWithType> metody slouží k přeložení vazby do jednoho člena. **Binder.BindToMethod** také obsahuje vlastnost řešení prostřednictvím **získat** a **nastavit** přístupové objekty vlastnosti.  
  
 **BindToMethod** vrátí <xref:System.Reflection.MethodBase> k vyvolání, nebo odkaz s hodnotou null (**nic** v jazyce Visual Basic) Pokud žádná taková volání je možné. **MethodBase** vrátit hodnotu nemusí být jedna z nich obsažené v *odpovídat* parametr, který sice obvyklý případ.  
  
 Když jsou v něm ByRef argumenty, volající chtít získat zpět. Proto **vazač** umožňuje klientovi mapování pole argumentů zpět do původní podobě, pokud **BindToMethod** se s nimi manipulovat, pole argumentů. Chcete-li to provést, musí být zaručena volající, že je pořadí argumentů beze změny. Při předávání argumentů podle názvu, **vazač** změní pole argumentů a který je co vidí volající. Další informace naleznete v tématu <xref:System.Reflection.Binder.ReorderArgumentArray%2A?displayProperty=nameWithType>.  
  
 Sadu členů k dispozici jsou tyto členy v typ nebo všechny základní typ definovaný. Pokud <xref:System.Reflection.BindingFlags> je zadán, bude vrácen členy jakékoli usnadnění v sadě. Pokud **BindingFlags.NonPublic** není zadán, vazač musí vynucovat pravidla usnadnění přístupu. Při zadávání **veřejné** nebo **NonPublic** příznak vazba, je třeba zadat také **Instance** nebo **statické** vazby příznak nebo ne členy, bude vrácen.  
  
 Pokud existuje jenom jednoho člena se zadaným názvem, bez zpětného volání je nezbytné a vazba se provádí na dané metody. Případ 1 příklad kódu ukazuje tento bod: pouze jeden **PrintBob** metoda je k dispozici, a proto je potřeba bez zpětného volání.  
  
 Pokud existuje více než jednoho člena v sadě k dispozici, se budou předávat všechny tyto metody **BindToMethod**, který vybere odpovídající metodu a vrátí ji. V případě 2 v příkladu kódu, existují dvě metody s názvem **PrintValue**. Ve volání je vybrán odpovídající metodu **BindToMethod**.  
  
 <xref:System.Reflection.Binder.ChangeType%2A>provede převod argument (převod typu), který převádí skutečné argumenty typu formální argumenty vybrané metody. **ChangeType –** je volána pro každý argument i v případě, že typy přesně shodují.  
  
 V případě 3 z příkladu kódu, skutečný argument typu **řetězec** s hodnotou "5.5" předaný metodě s argumentem formální typu **dvojité**. Volání úspěšné musí být řetězcovou hodnotu "5.5" převést na dvojitou hodnotu. **ChangeType –** provádí tento převod.  
  
 **ChangeType –** provádí pouze beze ztrát nebo [rozšiřující coercions](../../../docs/standard/base-types/type-conversion.md), jak je znázorněno v následující tabulce.  
  
|Typ zdroje|Cílový typ|  
|-----------------|-----------------|  
|Jakýkoli typ|Jeho základní typ|  
|Jakýkoli typ|Rozhraní se implementuje|  
|Char|UInt16, UInt32, Int32, UInt64, Int64, jedna Double|  
|Byte|Char, UInt32, UInt16, Int16, Int32, UInt64, Int64, jedna Double|  
|SByte|Int16, Int32, Int64, jedna Double|  
|UInt16|UInt32, Int32, Int64, UInt64 jednotné Double|  
|Int16|Int32, Int64, jedna Double|  
|UInt32|UInt64, Int64, jedna Double|  
|Int32|Int64, jedinou dvakrát|  
|UInt64|Jednoduché, Double|  
|Int64|Jednoduché, Double|  
|Single|Double|  
|Typ nereferenční|Typ odkazu|  
  
 <xref:System.Type> Třída má **získat** metody, které používají parametry typu **vazač** odkazy na konkrétní člena. <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType>, <xref:System.Type.GetMethod%2A?displayProperty=nameWithType>, a <xref:System.Type.GetProperty%2A?displayProperty=nameWithType> vyhledejte konkrétní člen má aktuální typ tím, že poskytuje informace o podpis pro tento člen. <xref:System.Reflection.Binder.SelectMethod%2A?displayProperty=nameWithType>a <xref:System.Reflection.Binder.SelectProperty%2A?displayProperty=nameWithType> se nazývají zpět k vyberte danou podpis informace odpovídající metody.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
 [Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [Převod typů v rozhraní .NET Framework](../../../docs/standard/base-types/type-conversion.md)
