---
title: Dynamické načtení a použití typů
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8254d3de7dc282edb8ebe8bf0dd71ce1c943322d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689205"
---
# <a name="dynamically-loading-and-using-types"></a>Dynamické načtení a použití typů
Reflexe poskytuje infrastrukturu pomocí kompilátorů jazyka, jako [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] a JScript implementace implicitní pozdní vazbu. Vazba je proces vyhledání deklarace (to znamená, implementace), která odpovídá jednoznačně zadaného typu. Když tento proces se provádí v době běhu, spíše než v době kompilace, je volána pozdní vazbu. [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] Umožňuje použít implicitní pozdní vazba v kódu; Kompilátor jazyka Visual Basic volá metodu helper, který používá reflexi k získání typu objektu. Argumenty předané do metody helper způsobit vhodná metoda k vyvolání za běhu. Tyto argumenty jsou instance (objekt), na kterém se má vyvolat metodu, název vyvolaná metoda (string) a argumenty předány volané metodě (pole objektů).  
  
 V následujícím příkladu kompilátor jazyka Visual Basic pomocí reflexe implicitně zavolá metodu na objekt, jehož typ není znám v době kompilace. A **HelloWorld** třída nemá **PrintHello** metodu, která vytiskne "Hello World" zřetězená s nějaký text, který je předán **PrintHello** metody. **PrintHello** metodu s názvem v tomto příkladu je ve skutečnosti <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>; umožňuje kódu jazyka Visual Basic **PrintHello** metoda k vyvolání, jako by byly při kompilaci známý typ objektu (helloObj) čas (časná vazba) místo za běhu (pozdní vazby).  
  
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
 Kromě používán implicitně kompilátory pozdní vazby, reflexe lze explicitně v kódu k provedení pozdní vazbu.  
  
 [Společného jazykového modulu runtime](../../../docs/standard/clr.md) podporuje více programovacích jazyků a pravidel vazby z těchto jazyků se liší. V případě časné vazby můžete generátory kódu úplnou kontrolu nad touto vazbou. Pozdní vazba prostřednictvím reflexe, musí být kontrolován vazby přizpůsobené vazbou. <xref:System.Reflection.Binder> Třída poskytuje vlastní ovládací prvek člena, výběru a vyvolání.  
  
 Použití vlastní vazby, můžete načíst sestavení v době běhu, získat informace o typech sestavení, zadejte požadovaný typ a poté vyvolat metody nebo přístup pole nebo vlastnosti na typu. Tato technika je užitečná, pokud neznáte typ objektu v době kompilace, jako je například, pokud je typ objektu závislý na vstup uživatele.  
  
 Následující příklad ukazuje jednoduchý vlastní vázací objekt, který obsahuje převod typu argumentu. Kód pro `Simple_Type.dll` předchází hlavní příklad. Je potřeba vytvořit `Simple_Type.dll` a poté zahrnout na ni odkaz v projektu v okamžiku sestavení.  
  
 [!code-cpp[Conceptual.Types.Dynamic#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.Dynamic#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.Dynamic#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source1.vb#1)]  
  
### <a name="invokemember-and-createinstance"></a>Metodu InvokeMember a CreateInstance  
 Použití <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType> se vyvolat člena typu. **CreateInstance** různé metody třídy, jako například <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> a <xref:System.Reflection.Assembly.CreateInstance%2A?displayProperty=nameWithType>, jsou specializované formy **metodu InvokeMember** , vytváření nových instancí zadaného typu. **Vazače** třída se používá pro překlad IP adres a argument vynucení přetížení v těchto metod.  
  
 Následující příklad ukazuje tři možné kombinace argumentů konverze (převod typu) a výběr členů. V případě 1 je potřeba žádný argument člena nebo konverze za výběr. V případě 2 je potřeba pouze výběr členů. V případě 3 je potřeba pouze argument vynucení.  
  
 [!code-cpp[Conceptual.Types.Dynamic#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.Dynamic#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.Dynamic#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source2.vb#2)]  
  
 Řešení přetížení je nutné, když je k dispozici více než jednoho člena se stejným názvem. <xref:System.Reflection.Binder.BindToMethod%2A?displayProperty=nameWithType> a <xref:System.Reflection.Binder.BindToField%2A?displayProperty=nameWithType> metody se používají k vyřešení vazby na jeden člen. **Binder.BindToMethod** také poskytuje vlastnost řešení prostřednictvím **získat** a **nastavit** přistupující objekty vlastnosti.  
  
 **BindToMethod** vrátí <xref:System.Reflection.MethodBase> k vyvolání, nebo odkaz s hodnotou null (**nic** v jazyce Visual Basic) Pokud žádná taková volání je možné. **MethodBase** vrátit hodnota nemusí být jedna z těchto součástí *odpovídat* parametr, i když to je obvyklý případ.  
  
 Když jsou k dispozici argumenty ByRef, volající může být vhodné získat zpět. Proto **vazač** umožňuje klientovi mapování pole argumentů zpět do původní podobě, pokud **BindToMethod** má manipulovat pole argumentů. Pokud to chcete udělat, musí být zaručena volajícímu, že pořadí argumentů je beze změny. Pokud argumenty jsou předány podle názvu, **vazače** změní pořadí pole argumentů, který je co uvidí volající. Další informace naleznete v tématu <xref:System.Reflection.Binder.ReorderArgumentArray%2A?displayProperty=nameWithType>.  
  
 Sada Dostupní členové jsou tyto členy definované podle typu nebo jakékoli základního typu. Pokud <xref:System.Reflection.BindingFlags> není zadán, vrátí se členy jakékoli přístupnosti v sadě. Pokud **BindingFlags.NonPublic** není zadán, vazače musí vynucovat pravidla přístupu. Při zadávání **veřejné** nebo **NonPublic** příznak vazby, musíte zadat také **Instance** nebo **statické** vazby příznak nebo ne Vrátí se členy.  
  
 Pokud existuje jenom jeden člen se zadaným názvem, bez zpětného volání je nezbytné a vazbu se provádí v této metodě. Případ 1 příklad kódu to znázorňuje: Pouze jeden **PrintBob** metoda je k dispozici, a proto je potřeba bez zpětného volání.  
  
 Pokud je k dispozici v sadě více než jednoho člena, všechny tyto metody jsou předány **BindToMethod**, který vybere odpovídající metodu a vrátí jej. V případě 2 příklad kódu, existují dvě metody s názvem **PrintValue**. Ve volání je vybrána odpovídající metodu **BindToMethod**.  
  
 <xref:System.Reflection.Binder.ChangeType%2A> provádí převod argumentu (převod typu), který převádí skutečné argumenty typu formální argumenty vybrané metody. **ChangeType** je volána pro každý argument i v případě, že typy přesně shodovat.  
  
 V případě 3 uvedeném příkladu kódu skutečný argument typu **řetězec** s hodnotou "5.5" je předán metodě s formální argument typu **Double**. Volání úspěšné musí být řetězcovou hodnotu "5.5" převést na dvojitou hodnotu. **ChangeType** provede tento převod.  
  
 **ChangeType** provádí pouze beze ztrát nebo [rozšiřující převody](../../../docs/standard/base-types/type-conversion.md), jak je znázorněno v následující tabulce.  
  
|Typ zdroje|Cílový typ|  
|-----------------|-----------------|  
|Jakýkoli typ|Jeho základní typ|  
|Jakýkoli typ|Rozhraní se implementuje|  
|Char|UInt16, UInt32, Int32, UInt64, Int64, Single, Double|  
|Byte|Char, UInt16, Int16, UInt32, Int32, UInt64, Int64, Single, Double|  
|SByte|Int16, Int32, Int64, Single, Double|  
|UInt16|UInt32, Int32, UInt64, Int64, jednoduché, Double|  
|Int16|Int32, Int64, Single, Double|  
|UInt32|UInt64, Int64, Single, Double|  
|Int32|Int64, Single, dvakrát|  
|UInt64|Jednoduché, Double|  
|Int64|Jednoduché, Double|  
|Single|Double|  
|Typ nereferenční|Typ odkazu|  
  
 <xref:System.Type> Třída má **získat** metody, které používají parametry typu **vazače** odkazy na určitého člena. <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType>, <xref:System.Type.GetMethod%2A?displayProperty=nameWithType>, a <xref:System.Type.GetProperty%2A?displayProperty=nameWithType> vyhledejte konkrétní členem aktuální typu tím, že poskytuje informace o podpisu pro tohoto člena. <xref:System.Reflection.Binder.SelectMethod%2A?displayProperty=nameWithType> a <xref:System.Reflection.Binder.SelectProperty%2A?displayProperty=nameWithType> se nazývají zpět k vyberte daným podpisem informace z odpovídající metody.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- [Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Převod typů v rozhraní .NET Framework](../../../docs/standard/base-types/type-conversion.md)
