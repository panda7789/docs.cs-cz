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
ms.openlocfilehash: 940f334ec6a42c4d8da461d634051ff979b8f98d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130266"
---
# <a name="dynamically-loading-and-using-types"></a>Dynamické načtení a použití typů
Reflexe poskytuje infrastrukturu využívanou kompilátory jazyka k implementaci implicitní pozdní vazby. Vazba je proces vyhledávání deklarace (to znamená implementace), která odpovídá jedinečnému zadanému typu. V případě, že tento proces probíhá v době běhu, nikoli v době kompilace, se nazývá pozdní vazba. Visual Basic umožňuje použít implicitní pozdní vazby v kódu; Kompilátor Visual Basic volá pomocnou metodu, která používá reflexi k získání typu objektu. Argumenty předané do pomocné metody způsobí, že příslušná metoda bude vyvolána v době běhu. Tyto argumenty jsou instance (objekt), na které se má vyvolat metoda, název vyvolané metody (řetězec) a argumenty předané vyvolané metodě (pole objektů).  
  
 V následujícím příkladu kompilátor Visual Basic používá reflexi implicitně k volání metody u objektu, jehož typ není v době kompilace znám. Třída **HelloWorld** má metodu **PrintHello** , která vypisuje "Hello World" zřetězené s nějakým textem, který je předán metodě **PrintHello** . Metoda **PrintHello** , která je volána v tomto příkladu, je ve skutečnosti <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>; kód Visual Basic umožňuje vyvolání metody **PrintHello** , jako by byl typ objektu (helloObj) známý v době kompilace (počáteční vazba) místo v době běhu (pozdní vazba).  
  
```vb
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
 Kromě implicitního použití kompilátory pro pozdní vazby lze odraz použít explicitně v kódu k provedení pozdní vazby.  
  
 Modul [CLR (Common Language Runtime)](../../standard/clr.md) podporuje více programovacích jazyků a pravidla vazeb těchto jazyků se liší. V případě předčasného vázání můžou generátory kódu úplně řídit tuto vazbu. V pozdní vazbě prostřednictvím reflexe však musí být vazba řízena přizpůsobenou vazbou. Třída <xref:System.Reflection.Binder> poskytuje vlastní ovládací prvek výběru a volání členů.  
  
 Pomocí vlastní vazby můžete načíst sestavení za běhu, získat informace o typech v tomto sestavení, určit typ, který chcete, a poté vyvolat metody nebo přístupová pole nebo vlastnosti pro daný typ. Tato technika je užitečná, pokud neznáte typ objektu v době kompilace, například když je typ objektu závislý na vstupu uživatele.  
  
 Následující příklad ukazuje jednoduchý vlastní pořadač, který neposkytuje převod typu argumentu. Kód pro `Simple_Type.dll` předchází hlavnímu příkladu. Nezapomeňte sestavit `Simple_Type.dll` a potom do projektu zahrnout odkaz na projekt v čase sestavení.  
  
 [!code-cpp[Conceptual.Types.Dynamic#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.Dynamic#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.Dynamic#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source1.vb#1)]  
  
### <a name="invokemember-and-createinstance"></a>Metodu InvokeMember a CreateInstance  
 Použijte <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType> k vyvolání člena typu. Metody **CreateInstance** různých tříd, například <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> a <xref:System.Reflection.Assembly.CreateInstance%2A?displayProperty=nameWithType>, jsou specializované formuláře **metodu InvokeMember** , které vytvářejí nové instance zadaného typu. Třída **pořadače** se používá pro rozlišení přetěžování a pro převod argumentů v těchto metodách.  
  
 Následující příklad ukazuje tři možné kombinace argumentu konverze (převod typu) a výběr členů. V případě 1 není nutné provádět převod argumentů ani výběr členů. V případě 2 se vyžaduje jenom výběr členů. V případě 3 je nutná pouze konverze argumentu.  
  
 [!code-cpp[Conceptual.Types.Dynamic#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.Dynamic#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.Dynamic#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source2.vb#2)]  
  
 Je-li k dispozici více než jeden člen se stejným názvem, je nutné Rozlišení přetěžování. Metody <xref:System.Reflection.Binder.BindToMethod%2A?displayProperty=nameWithType> a <xref:System.Reflection.Binder.BindToField%2A?displayProperty=nameWithType> slouží k překladu vazby na jeden člen. **Binder. BindToMethod** také poskytuje řešení vlastností prostřednictvím přístupových objektů **Get** a **set** vlastnosti.  
  
 **BindToMethod** vrací <xref:System.Reflection.MethodBase> k vyvolání nebo odkaz s hodnotou null (**Nothing** v Visual Basic), pokud žádné takové vyvolání není možné. Návratová hodnota **tokenem MethodBase** nemusí být jednou z hodnot obsažených v parametru *Match* , i když je to běžný případ.  
  
 Pokud jsou argumenty ByRef přítomny, volající ho může chtít vrátit zpátky. Proto aplikace **Binder** umožňuje klientovi mapovat pole argumentů zpátky na původní formulář, pokud **BindToMethod** pracuje s polem argumentů. Aby to bylo možné, volající musí zaručit, že pořadí argumentů je beze změny. Když jsou argumenty předány podle názvu, **Binder** přeuspořádat pole argumentu a to je to, co se volající zobrazí. Další informace najdete v tématu <xref:System.Reflection.Binder.ReorderArgumentArray%2A?displayProperty=nameWithType>.  
  
 Sada dostupných členů je členy, kteří jsou definováni v typu nebo jakémkoli základním typu. Je-li zadán <xref:System.Reflection.BindingFlags>, budou v sadě vráceny členové jakékoliv přístupnosti. Pokud se nezadá **příznak BindingFlags. NonPublic** , musí si pořadač vynutilit pravidla přístupnosti. Když zadáte příznak **Public** nebo **NonPublic** Binding, musíte také zadat příznak **instance** nebo **statické** vazby, jinak nebudou vráceny žádné členy.  
  
 Pokud je k dispozici pouze jeden člen daného názvu, není nutné žádné zpětné volání a vazba je provedena na této metodě. Případ 1 příkladu kódu ukazuje tento bod: je k dispozici pouze jedna metoda **PrintBob** , a proto není nutné žádné zpětné volání.  
  
 Pokud je v sadě k dispozici více než jeden člen, všechny tyto metody jsou předány do **BindToMethod**, který vybere příslušnou metodu a vrátí ji. V případě 2 příkladu kódu existují dvě metody s názvem **PrintValue**. Příslušná metoda je vybrána voláním metody **BindToMethod**.  
  
 <xref:System.Reflection.Binder.ChangeType%2A> provádí převod argumentů (převod typu), který převede skutečné argumenty na typ formálních argumentů vybrané metody. **ChangeType** je volána pro každý argument i v případě, že se typy shodují přesně.  
  
 V případě 3 příkladu kódu je skutečný argument typu **String** s hodnotou "5,5" předán metodě se formálním argumentem typu **Double**. Aby bylo volání úspěšné, Řetězcová hodnota "5,5" musí být převedena na dvojitou hodnotu. **ChangeType** provede tento převod.  
  
 **ChangeType** provádí pouze bezeztrátové nebo [rozšiřování převodů](../../standard/base-types/type-conversion.md), jak je znázorněno v následující tabulce.  
  
|Typ zdroje|Cílový typ|  
|-----------------|-----------------|  
|Libovolný typ|Jeho základní typ|  
|Libovolný typ|Rozhraní, které implementuje|  
|Char|UInt16, UInt32, Int32, UInt64, Int64, Single, Double|  
|Byte|Char, UInt16, Int16, UInt32, Int32, UInt64, Int64, Single, Double|  
|SByte|Int16, Int32, Int64, Single, Double|  
|UInt16|UInt32, Int32, UInt64, Int64, Single, Double|  
|Int16|Int32, Int64, Single, Double|  
|UInt32|UInt64, Int64, Single, Double|  
|Int32|Int64, Single, Double|  
|UInt64|Jednoduchá, Dvojitá|  
|Int64|Jednoduchá, Dvojitá|  
|Single|Double|  
|Typ neodkazování|typ odkazu|  
  
 Třída <xref:System.Type> má metody **Get** , které používají parametry typu **Binder** k překladu odkazů na konkrétního člena. <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType>, <xref:System.Type.GetMethod%2A?displayProperty=nameWithType>a <xref:System.Type.GetProperty%2A?displayProperty=nameWithType> vyhledat konkrétního člena aktuálního typu tím, že poskytnete informace o podpisu pro daného člena. <xref:System.Reflection.Binder.SelectMethod%2A?displayProperty=nameWithType> a <xref:System.Reflection.Binder.SelectProperty%2A?displayProperty=nameWithType> se zavolají zpátky a vyberte příslušné informace o podpisu příslušných metod.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- [Zobrazení informací o typu](viewing-type-information.md)
- [Převod typu v .NET Framework](../../standard/base-types/type-conversion.md)
