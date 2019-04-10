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
ms.openlocfilehash: c7c2956a222a47cea36abbc2f21da2d7e2061e09
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314526"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Postupy: Připojení delegáta pomocí reflexe
Při použití reflexe načtení a spuštění sestavení nelze použít jazykové funkce, jako C# `+=` operátor nebo Visual Basic [AddHandler – příkaz](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) k připojení události. Následující postupy ukazují, jak připojit existující metodu na událost tím, že získáme všechny nezbytné typy prostřednictvím reflexe a vytvoření dynamickou metodu pomocí operace reflection emit a zapojit ji až událost.  
  
> [!NOTE]
>  Dalším způsobem, jak připojit delegát zpracování událostí, naleznete v části příklad kódu pro <xref:System.Reflection.EventInfo.AddEventHandler%2A> metodu <xref:System.Reflection.EventInfo> třídy.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>K připojení delegáta pomocí reflexe  
  
1. Načtení sestavení obsahující typ, který vyvolává události. Sestavení jsou obvykle načtena s <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody. Pro zjednodušení tento příklad používá odvozený formulář v nástrojích pro aktuální sestavení, takže <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metoda se používá k načtení aktuální sestavení.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. Získání <xref:System.Type> objekt představující typ a vytvořte její instanci typu. <xref:System.Activator.CreateInstance%28System.Type%29> Metoda se používá v následujícím kódu, protože formulář nemá výchozí konstruktor. Existuje několik dalších přetížení <xref:System.Activator.CreateInstance%2A> metodu, která můžete použít, pokud typ při vytváření nemá výchozí konstruktor. Nová instance se ukládá jako typ <xref:System.Object> udržovat fiction této není nic vědět o sestavení. (Reflexe umožňuje získat typy v sestavení bez znalosti jejich názvy předem.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. Získat <xref:System.Reflection.EventInfo> objekt představující události a použít <xref:System.Reflection.EventInfo.EventHandlerType%2A> vlastnost k získání typu delegát, pomocí něhož chcete zpracovat událost. V následujícím kódu <xref:System.Reflection.EventInfo> pro <xref:System.Windows.Forms.Control.Click> získat události.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. Získání <xref:System.Reflection.MethodInfo> objekt reprezentující metodu, která zpracovává událost. Kód dokončení programu v oddíle Příklad dále v tomto tématu obsahuje metodu, která se shoduje se signaturou <xref:System.EventHandler> delegovat, která zpracovává <xref:System.Windows.Forms.Control.Click> události, ale dají vygenerovat také dynamických metod v době běhu. Podrobnosti najdete v tématu souvisejícím postupu pro vygenerování obslužné rutiny události v době běhu pomocí dynamické metody.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. Vytvoření instance delegáta pomocí <xref:System.Delegate.CreateDelegate%2A> metody. Tato metoda je statická (`Shared` v jazyce Visual Basic), takže je nutné zadat typ delegáta. Pomocí přetížení <xref:System.Delegate.CreateDelegate%2A> trvají <xref:System.Reflection.MethodInfo> se doporučuje.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. Získejte `add` přístupové metody a použít ho k připojení události. Všechny události mají `add` přístupového objektu a `remove` přístupový objekt, který jsou skryty pomocí syntaxe vysoké úrovně jazyků. Například C# používá `+=` k připojení události a jazyk Visual Basic používá operátor [AddHandler – příkaz](~/docs/visual-basic/language-reference/statements/addhandler-statement.md). Následující kód získá `add` přistupující objekt <xref:System.Windows.Forms.Control.Click> událostí a spustí ho s pozdní vazbou, předejte instanci delegáta. Argumenty musí být předán jako pole.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. Testovací událost. Následující kód ukazuje formulář definovaný v příkladu kódu. Kliknutí na formuláři vyvolá obslužnou rutinu události.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Ke generování obslužné rutiny události v době běhu pomocí dynamické metody  
  
1. Metody obslužné rutiny události mohou být generovány v době běhu pomocí zjednodušené dynamických metod a emitování reflexe. K vytvoření obslužné rutiny události, budete potřebovat návratový typ a typy parametrů delegáta. Ty můžete získat prozkoumáním delegáta `Invoke` metody. Následující kód používá `GetDelegateReturnType` a `GetDelegateParameterTypes` metody pro získání těchto informací. Kód pro tyto metody lze nalézt v oddílu příklad dále v tomto tématu.  
  
     Není nutné pojmenovat <xref:System.Reflection.Emit.DynamicMethod>, takže se dají použít prázdný řetězec. V následujícím kódu, posledním argumentem přidruží dynamickou metodu s aktuálním typem delegáta poskytuje přístup k všechny veřejné a soukromé členy `Example` třídy.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. Vygenerování těla metody. Tato metoda načte řetězec, volá přetížení <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metodu, která přebírá řetězec, zobrazí návratová hodnota ze zásobníku (protože obslužná rutina nemá žádný návratový typ) a vrátí. Další informace o generování dynamických metod najdete v tématu [jak: Definování a provádění dynamických metod](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. Dokončení dynamickou metodu. voláním jeho <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metoda. Použití `add` přístupový objekt pro přidání do seznamu vyvolání události, delegát.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. Testovací událost. Následující kód načte formulář definovaný v příkladu kódu. Kliknutí na formuláři vyvolá obslužnou rutinu předdefinované události a obslužná rutina události emitovaný.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak připojit existující metodu na událost pomocí reflexe a také způsob použití <xref:System.Reflection.Emit.DynamicMethod> třídu pro generování metodu v době běhu a zapojit ji do události.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Obsahuje kód jazyka C# `using` příkazy (`Imports` v jazyce Visual Basic) nezbytné pro kompilaci.  
  
-   Žádné odkazy na další sestavení jsou požadovány pro kompilaci z příkazového řádku. V sadě Visual Studio musíte přidat odkaz na System.Windows.Forms.dll, protože v tomto příkladu je konzolová aplikace.  
  
-   Kompilace kódu do příkazového řádku pomocí csc.exe a vbc.exe, cl.exe. Ke kompilaci kódu v sadě Visual Studio, umístěte ho do šablony projektu konzolové aplikace.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [Postupy: Definování a provádění dynamických metod](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)
- [Reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)
