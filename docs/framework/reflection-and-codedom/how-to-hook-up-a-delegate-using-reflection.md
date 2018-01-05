---
title: "Postupy: Připojení delegáta pomocí reflexe"
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
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ff800eb78b07fc79193c2aa8cb71a461be2fc1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Postupy: Připojení delegáta pomocí reflexe
Pokud používáte reflexe načíst a spuštění sestavení, nelze použít jazykové funkce jako jazyka C# `+=` operátor nebo Visual Basic [AddHandler – příkaz](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) spojit události. Následující postupy ukazují, jak spojit stávající metodu pro událost získáním všechny potřebné typy prostřednictvím reflexe a postup vytvoření dynamické metody pomocí reflexe emitování a propojte ho až událost.  
  
> [!NOTE]
>  Pro další způsob spojit delegáta zpracování událostí, podívejte se na příklad kódu pro <xref:System.Reflection.EventInfo.AddEventHandler%2A> metodu <xref:System.Reflection.EventInfo> třídy.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Chcete-li připojení delegáta pomocí reflexe  
  
1.  Načtení sestavení, které obsahuje typ, který vyvolává události. Sestavení jsou obvykle načíst pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda. Pro zjednodušení tento příklad používá odvozené formuláře v aktuální sestavení, proto <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metoda se používá k načtení aktuální sestavení.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2.  Získání <xref:System.Type> objekt představující typ a vytvořit instanci typu. <xref:System.Activator.CreateInstance%28System.Type%29> Metoda se používá v následujícím kódu, protože formulář má výchozí konstruktor. Existuje několik dalších přetížení <xref:System.Activator.CreateInstance%2A> metoda, kterou můžete použít, pokud typ vytváříte nemá výchozí konstruktor. Nová instance je uložený jako typ <xref:System.Object> udržovat fiction se označuje tento není nic o sestavení. (Reflexe umožňuje získat typy v sestavení bez znalosti jejich názvy předem.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3.  Získat <xref:System.Reflection.EventInfo> objekt reprezentující události a použít <xref:System.Reflection.EventInfo.EventHandlerType%2A> vlastnost k získání typu delegát používá ke zpracování události. Následující kód <xref:System.Reflection.EventInfo> pro <xref:System.Windows.Forms.Control.Click> se získávají událostí.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4.  Získání <xref:System.Reflection.MethodInfo> objektu, který představuje metodu, která zpracovává událost. Kód dokončení programu v části Příklad později v tomto tématu obsahuje metodu, která odpovídá podpis <xref:System.EventHandler> delegovat, která zpracovává <xref:System.Windows.Forms.Control.Click> událostí, ale můžete také vygenerovat dynamických metod v době běhu. Podrobnosti najdete v tématu doprovodné postupu pro vytvoření obslužné rutiny události v době běhu pomocí dynamické metody.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5.  Vytvořte instanci delegáta pomocí <xref:System.Delegate.CreateDelegate%2A> metoda. Tato metoda je statická (`Shared` v jazyce Visual Basic), takže je nutné zadat typ delegáta. Pomocí přetížení <xref:System.Delegate.CreateDelegate%2A> trvají <xref:System.Reflection.MethodInfo> se doporučuje.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6.  Získat `add` metoda přistupujícího objektu a vyvolání ho spojit události. Mají všechny události `add` přistupujícího objektu a `remove` přistupujícího objektu, který skryty pomocí syntaxe vysoké úrovně jazyky. Například C# používá `+=` operátor spojit události a používá jazyka Visual Basic [AddHandler – příkaz](~/docs/visual-basic/language-reference/statements/addhandler-statement.md). Následující kód získá `add` přistupujícího <xref:System.Windows.Forms.Control.Click> událostí a vyvolá ho pozdní vazbu předávání v instanci delegáta. Argumenty, které musí být předán jako pole.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7.  Otestujte události. Následující kód ukazuje formuláře definované v příkladu kódu. Obslužné rutiny události kliknutí na formuláři vyvolá.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Generovat obslužné rutiny události v době běhu pomocí dynamické metody  
  
1.  Metody obslužné rutiny události může být generována v době běhu pomocí lightweight dynamických metod a emitování reflexe. K vytvoření obslužné rutiny události, musíte návratový typ a typy parametrů delegáta. To můžete získat tak, že prověří delegáta `Invoke` metoda. Následující kód používá `GetDelegateReturnType` a `GetDelegateParameterTypes` metody pro získání těchto informací. Kód pro tyto metody naleznete v části Příklad později v tomto tématu.  
  
     Není nutné pojmenovat <xref:System.Reflection.Emit.DynamicMethod>, takže lze prázdný řetězec. V následujícím kódu, poslední argument přidruží dynamické metoda má aktuální typ udělení delegát přístup k všechny veřejné a soukromé členy `Example` třídy.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2.  Generovat těla metody. Tato metoda načte řetězec, volá přetížení <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metoda, která přebírá řetězec, POP návratovou hodnotu ze zásobníku (protože obslužná rutina nemá žádný návratový typ) a vrátí. Další informace o Emitování dynamických metod najdete v tématu [postupy: definování a spouštět dynamické metody](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3.  Dokončení dynamické metoda voláním jeho <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metoda. Použití `add` přistupujícího objektu delegát přidat do seznamu vyvolání události.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4.  Otestujte události. Následující kód načte formuláře definované v příkladu kódu. Klepnutím na formulář vyvolá obslužnou rutinu události předdefinované a obslužné rutiny emitovaného události.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak spojit stávající metodu pro událost pomocí reflexe a také způsob použití <xref:System.Reflection.Emit.DynamicMethod> třídy emitování metodu v době běhu a propojte ho až událost.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Obsahuje kód jazyka C# `using` příkazy (`Imports` v jazyce Visual Basic) potřebné pro kompilaci.  
  
-   Žádné odkazy na další sestavení jsou požadovány pro kompilaci z příkazového řádku. V sadě Visual Studio musíte přidat odkaz na System.Windows.Forms.dll, protože v tomto příkladu je konzolová aplikace.  
  
-   Kompilace kódu na příkazovém řádku pomocí csc.exe, vbc.exe nebo cl.exe. Kompilace kódu v sadě Visual Studio, umístěte ho do šablony projektu konzolové aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Emit.DynamicMethod>  
 <xref:System.Activator.CreateInstance%2A>  
 <xref:System.Delegate.CreateDelegate%2A>  
 [Postupy: Definování a provádění dynamických metod](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)  
 [Reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)
