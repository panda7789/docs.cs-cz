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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b07c3eb9d96bb6f675a6a2ca742cc9bdf3c3826
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364063"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Postupy: Připojení delegáta pomocí reflexe
Použijete-li reflexi pro načtení a spuštění sestavení, nemůžete použít C# `+=` funkce jazyka jako operátor nebo [příkaz Visual Basic AddHandler](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) k připojení událostí. Následující postupy ukazují, jak připojit existující metodu k události tím, že získá všechny nezbytné typy prostřednictvím reflexe a jak vytvořit dynamickou metodu pomocí generování reflexe a připojit ji k události.  
  
> [!NOTE]
>  Další způsob, jak připojit delegáta zpracování událostí, naleznete v příkladu kódu pro <xref:System.Reflection.EventInfo.AddEventHandler%2A> metodu <xref:System.Reflection.EventInfo> třídy.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Připojení delegáta pomocí reflexe  
  
1. Načte sestavení, které obsahuje typ, který vyvolává události. Sestavení jsou obvykle načtena pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody. Chcete-li tento příklad jednoduché, je použit odvozený formulář v aktuálním sestavení, takže <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metoda slouží k načtení aktuálního sestavení.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <xref:System.Type> Získání objektu představujícího typ a vytvoření instance typu. <xref:System.Activator.CreateInstance%28System.Type%29> Metoda je použita v následujícím kódu, protože formulář obsahuje konstruktor bez parametrů. Existuje několik dalších přetížení <xref:System.Activator.CreateInstance%2A> metody, kterou můžete použít, pokud typ, který vytváříte, nemá konstruktor bez parametrů. Nová instance je uložena jako typ <xref:System.Object> pro zachování fiktivního, že pro sestavení není nic známé. (Reflexe umožňuje získat typy v sestavení, aniž byste museli znát jejich názvy předem.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. Získat objekt reprezentující událost a <xref:System.Reflection.EventInfo.EventHandlerType%2A> použít vlastnost k získání typu delegáta použitého ke zpracování události. <xref:System.Reflection.EventInfo> V následujícím kódu <xref:System.Reflection.EventInfo> je získána <xref:System.Windows.Forms.Control.Click> pro událost.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <xref:System.Reflection.MethodInfo> Získat objekt reprezentující metodu, která zpracovává událost. Úplný kód programu v příkladu níže v tomto tématu obsahuje metodu, která odpovídá signatuře <xref:System.EventHandler> delegáta, který <xref:System.Windows.Forms.Control.Click> zpracovává událost, ale můžete také generovat dynamické metody za běhu. Podrobnosti naleznete v doprovodné proceduře pro generování obslužné rutiny události v době běhu pomocí dynamické metody.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. Vytvořte instanci delegáta pomocí <xref:System.Delegate.CreateDelegate%2A> metody. Tato metoda je statická (`Shared` v Visual Basic), proto je nutné zadat typ delegáta. Použití přetížení <xref:System.Delegate.CreateDelegate%2A> , které <xref:System.Reflection.MethodInfo> přijímá, je doporučeno.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. `add` Získat přístupovou metodu a vyvolat ji pro zapojení události. Všechny události mají `add` přistupující objekt `remove` a přistupující objekt, který je skryt syntaxí jazyků vysoké úrovně. Například C# používá `+=` operátor k zapojení událostí a Visual Basic používá [příkaz AddHandler](~/docs/visual-basic/language-reference/statements/addhandler-statement.md). Následující kód získá `add` přistupující objekt <xref:System.Windows.Forms.Control.Click> události a vyvolá pozdní vazbu s předáním do instance delegáta. Argumenty musí být předány jako pole.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. Otestujte událost. Následující kód ukazuje formulář definovaný v příkladu kódu. Kliknutím na formulář se vyvolá obslužná rutina události.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Generování obslužné rutiny události v době běhu pomocí dynamické metody  
  
1. Metody obslužné rutiny události mohou být generovány v době běhu pomocí zjednodušených dynamických metod a generování reflexe. Chcete-li vytvořit obslužnou rutinu události, budete potřebovat návratový typ a typy parametrů delegáta. Ty lze získat prozkoumáním `Invoke` metody delegáta. Následující kód používá `GetDelegateReturnType` metody a `GetDelegateParameterTypes` k získání těchto informací. Kód pro tyto metody lze nalézt v části příklad dále v tomto tématu.  
  
     Není nutné pojmenovat <xref:System.Reflection.Emit.DynamicMethod>, aby bylo možné použít prázdný řetězec. V následujícím kódu poslední argument přidružuje dynamickou metodu k aktuálnímu typu, což dává delegátovi přístup ke všem veřejným a soukromým členům `Example` třídy.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. Vygeneruje tělo metody. Tato metoda načte řetězec, zavolá přetížení <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metody, která přijímá řetězec, vyvolá vrácenou hodnotu mimo zásobník (protože obslužná rutina nemá žádný návratový typ) a vrátí hodnotu. Další informace o generování dynamických metod naleznete v tématu [How to: Definujte a spusťte dynamické metody](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. Dokončete dynamickou metodu voláním <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> její metody. `add` Pomocí přístupového objektu přidejte delegáta do seznamu vyvolání pro událost.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. Otestujte událost. Následující kód načte formulář definovaný v příkladu kódu. Kliknutím na formulář se vyvolá předdefinovaná obslužná rutina události a obslužná rutina emitované události.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak připojit existující metodu k události pomocí reflexe a také jak použít <xref:System.Reflection.Emit.DynamicMethod> třídu k vygenerování metody v době běhu a jejímu zapojení do události.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [Postupy: Definování a provádění dynamických metod](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)
- [Reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)
