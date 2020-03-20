---
title: 'Postupy: Připojení delegáta pomocí reflexe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
ms.openlocfilehash: d748d9f8bdd0b4d831880548d4aceb1c77a0b0c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180508"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Postupy: Připojení delegáta pomocí reflexe
Při použití reflexe načíst a spustit sestavení, nelze použít `+=` funkce jazyka, jako je operátor C# nebo Visual Basic [AddHandler prohlášení](../../visual-basic/language-reference/statements/addhandler-statement.md) připojit události. Následující postupy ukazují, jak připojit existující metodu k události získáním všech potřebných typů prostřednictvím reflexe a jak vytvořit dynamickou metodu pomocí odrazu vyzařovat a připojit k události.  
  
> [!NOTE]
> Pro jiný způsob, jak připojit delegáta zpracování událostí, <xref:System.Reflection.EventInfo.AddEventHandler%2A> naleznete <xref:System.Reflection.EventInfo> v příkladu kódu pro metodu třídy.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Připojení delegáta pomocí reflexe  
  
1. Načtěte sestavení, které obsahuje typ, který vyvolává události. Sestavení jsou obvykle načteny <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodou. Chcete-li zachovat tento příklad jednoduché, odvozený formulář v <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> aktuální sestavě se používá, takže metoda se používá k načtení aktuální sestavení.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. Získejte <xref:System.Type> objekt představující typ a vytvořte instanci typu. Metoda <xref:System.Activator.CreateInstance%28System.Type%29> se používá v následujícím kódu, protože formulář má konstruktor bez parametrů. Existuje několik dalších přetížení <xref:System.Activator.CreateInstance%2A> metody, které můžete použít, pokud typ, který vytváříte nemá konstruktor bez parametrů. Nová instance je uložena jako typ <xref:System.Object> zachovat fikci, že nic není známo o sestavení. (Reflexe umožňuje získat typy v sestavení bez znalosti jejich názvy předem.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. Získejte <xref:System.Reflection.EventInfo> objekt představující událost a <xref:System.Reflection.EventInfo.EventHandlerType%2A> pomocí vlastnosti získat typ delegáta slouží ke zpracování události. V následujícím kódu <xref:System.Reflection.EventInfo> je <xref:System.Windows.Forms.Control.Click> získán a for the event.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. Získejte <xref:System.Reflection.MethodInfo> objekt představující metodu, která zpracovává událost. Úplný kód programu v části Příklad dále v tomto tématu <xref:System.EventHandler> obsahuje metodu, <xref:System.Windows.Forms.Control.Click> která odpovídá podpisu delegáta, který zpracovává událost, ale můžete také generovat dynamické metody za běhu. Podrobnosti naleznete v doprovodném postupu, pro generování obslužné rutiny události za běhu pomocí dynamické metody.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. Vytvořte instanci delegáta <xref:System.Delegate.CreateDelegate%2A> pomocí metody. Tato metoda je`Shared` statická ( v jazyce Visual Basic), takže musí být zadán typ delegáta. Použití <xref:System.Delegate.CreateDelegate%2A> přetížení, které se <xref:System.Reflection.MethodInfo> doporučuje.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. Získejte `add` přistupující metodu a vyvolat ji připojit událost. Všechny události `add` mají přistupující objekt a přistupující `remove` objekt, které jsou skryty syntaxí jazyků vysoké úrovně. Například C# používá `+=` operátor k připojení událostí a Visual Basic používá [AddHandler prohlášení](../../visual-basic/language-reference/statements/addhandler-statement.md). Následující kód získá `add` přistupující ho <xref:System.Windows.Forms.Control.Click> události a vyvolá ji pozdní vazbu, předávání v instanci delegáta. Argumenty musí být předány jako pole.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. Otestujte událost. Následující kód zobrazuje formulář definovaný v příkladu kódu. Klepnutím na formulář vyvoláte obslužnou rutinu události.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Generování obslužné rutiny události za běhu pomocí dynamické metody  
  
1. Metody obslužné rutiny událostí lze generovat za běhu pomocí zjednodušené dynamické metody a odraz emit. Chcete-li vytvořit obslužnou rutinu události, potřebujete návratový typ a typy parametrů delegáta. Ty lze získat kontrolou metody delegáta. `Invoke` Následující kód používá `GetDelegateReturnType` `GetDelegateParameterTypes` metody a k získání těchto informací. Kód pro tyto metody naleznete v části Příklad dále v tomto tématu.  
  
     Není nutné pojmenovat <xref:System.Reflection.Emit.DynamicMethod>, takže lze použít prázdný řetězec. V následujícím kódu poslední argument přidruží dynamickou metodu k aktuálnímu typu a poskytuje `Example` delegátovi přístup všem veřejným a soukromým členům třídy.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. Generovat tělo metody. Tato metoda načte řetězec, volá <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> přetížení metody, která přebírá řetězec, vyskočí vrácená hodnota ze zásobníku (protože obslužná rutina nemá žádný návratový typ) a vrátí. Další informace o vyzařování dynamických metod naleznete v [tématu How to: Define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. Dokončete dynamickou metodu voláním její <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody. Pomocí `add` přistupujícího seznamu přidejte delegáta do seznamu vyvolání události.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. Otestujte událost. Následující kód načte formulář definovaný v příkladu kódu. Kliknutím na formulář vyvoláte předdefinovanou obslužnou rutinu události i eemitovní obslužnou rutinu události.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak připojit existující metodu k události pomocí <xref:System.Reflection.Emit.DynamicMethod> reflexe a také jak použít třídu k vyzařování metody za běhu a připojit ji k události.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [Postupy: Definování a provádění dynamických metod](how-to-define-and-execute-dynamic-methods.md)
- [Reflexe](reflection.md)
