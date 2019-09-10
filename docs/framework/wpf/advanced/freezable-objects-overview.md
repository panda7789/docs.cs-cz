---
title: Přehled zablokovatelných objektů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
ms.openlocfilehash: 854565e28e646ef57658e2bfdb7326d8453448d2
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856068"
---
# <a name="freezable-objects-overview"></a>Přehled zablokovatelných objektů

V tomto tématu se dozvíte, jak efektivně <xref:System.Windows.Freezable> používat a vytvářet objekty, které poskytují speciální funkce, které mohou pomoci zlepšit výkon aplikace. Příklady objektů Freezable zahrnují štětce, pera, transformace, geometrií a animace.

<a name="whatisafreezable"></a>

## <a name="what-is-a-freezable"></a>Co je Freezable?

A <xref:System.Windows.Freezable> je speciální typ objektu, který má dva stavy: nezmrazené a zmrazené. Při nezmrazení se <xref:System.Windows.Freezable> zdá, že se chová jako jakýkoliv jiný objekt. Po zmrazení <xref:System.Windows.Freezable> již nelze upravovat.

<xref:System.Windows.Freezable> Poskytujeudálostupozorňujícípozorovatele<xref:System.Windows.Freezable.Changed> na jakékoli úpravy objektu. Zmrazení <xref:System.Windows.Freezable> může zlepšit jeho výkon, protože už nepotřebuje věnovat prostředky v oznámeních o změnách. Zmrazení <xref:System.Windows.Freezable> lze také sdílet mezi vlákny, zatímco nezmrazení <xref:System.Windows.Freezable> nemůže.

I když <xref:System.Windows.Freezable> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třída obsahuje mnoho aplikací, většina objektů v je v relaci s podsystémem grafiky. <xref:System.Windows.Freezable>

<xref:System.Windows.Freezable> Třída usnadňuje používání určitých grafických systémových objektů a může zvýšit výkon aplikace. Příklady typů, které dědí z <xref:System.Windows.Freezable> <xref:System.Windows.Media.Brush>zahrnuje třídy, <xref:System.Windows.Media.Transform>a <xref:System.Windows.Media.Geometry> . Vzhledem k tomu, že obsahují nespravované prostředky, systém musí tyto objekty monitorovat pro úpravy a následně aktualizovat odpovídající nespravované prostředky, pokud dojde ke změně původního objektu. I v případě, že ve skutečnosti neupravíte objekt systému grafiky, systém musí stále strávit některé prostředky, které sledují objekt, v případě, že ho změníte.

Předpokládejme například, že vytvoříte <xref:System.Windows.Media.SolidColorBrush> štětec a použijete ho k vykreslování pozadí tlačítka.

[!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
[!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]

Když je toto tlačítko vykresleno, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá dílčí systém grafiky informace, které jste zadali k vykreslení skupiny pixelů, aby bylo možné vytvořit vzhled tlačítka. I když jste použili barevný štětec, který popisuje, jak se má tlačítko vykreslit, váš barevný štětec ve skutečnosti neprovede malování. Grafický systém generuje rychlé objekty nízké úrovně pro tlačítko a štětec a jedná se o objekty, které se ve skutečnosti zobrazují na obrazovce.

Pokud jste změnili štětec, bude nutné tyto objekty nízké úrovně znovu vygenerovat. Třída Freezable je to, co umožňuje štětci najít odpovídající vygenerované objekty nízké úrovně a aktualizovat je při změně. Když je tato možnost povolená, bude se štětec považovat za nezmrazený.

<xref:System.Windows.Freezable.Freeze%2A> Metoda Freezable umožňuje zakázat tuto schopnost automatických aktualizací. Tuto metodu lze použít k tomu, aby se štětec stala "zmrazená", nebo neupravitelný.

> [!NOTE]
> Ne každý objekt Freezable může být zmrazen. Chcete-li se <xref:System.InvalidOperationException>vyhnout vyvolání, zkontrolujte hodnotu <xref:System.Windows.Freezable.CanFreeze%2A> vlastnosti objektu Freezable a určete, zda může být zmrazena před pokusem o její zablokování.

[!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
[!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]

Když už nepotřebujete měnit Freezable, zamrznutí poskytuje výhody pro výkon. Pokud jste v tomto příkladu zablokování štětce, grafický systém už ho nebude potřebovat ke sledování změn. Systém grafiky může také provádět další optimalizace, protože ví, že se štětec nemění.

> [!NOTE]
> Pro usnadnění práce objekty Freezable zůstanou nezmrazené, pokud je explicitně neuvolníte.

<a name="frozenfreezables"></a>

## <a name="using-freezables"></a>Použití Zablokovatelné

Použití nezmrazeného Freezable se podobá použití jiného typu objektu. V následujícím příkladu se barva a <xref:System.Windows.Media.SolidColorBrush> změní ze žluté na červenou po použití k vykreslení pozadí tlačítka. Grafický systém funguje na pozadí, aby při příštím obnovení obrazovky automaticky změnil tlačítko od žluté na červenou.

[!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
[!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]

### <a name="freezing-a-freezable"></a>Zmrazení Freezable

Chcete-li <xref:System.Windows.Freezable> provést neupravitelný způsob volání, <xref:System.Windows.Freezable.Freeze%2A> zavolejte jeho metodu. Při zablokování objektu, který obsahuje objekty Freezable, jsou tyto objekty také zmrazeny. Pokud například zadáte <xref:System.Windows.Media.PathGeometry>, hodnoty a segmenty, které obsahuje, by byly zmrazeny.

Freezable **nelze** zmrazit, pokud platí některá z následujících podmínek:

- Obsahuje animované nebo vlastnosti vázaného na data.

- Má vlastnosti nastavené dynamickým prostředkem. (Další informace o dynamických prostředcích najdete v tématu [zdroje XAML](xaml-resources.md) .)

- Obsahuje <xref:System.Windows.Freezable> dílčí objekty, které nelze ukotvit.

Pokud jsou tyto podmínky nepravdivé a nehodláte je upravovat <xref:System.Windows.Freezable>, měli byste je zmrazit, abyste získali výše popsané výhody výkonu.

Po volání <xref:System.Windows.Freezable.Freeze%2A> metody Freezable již nelze upravovat. Pokus o úpravu zmrazeného objektu způsobí, že <xref:System.InvalidOperationException> bude vyvolána výjimka. Následující kód vyvolá výjimku, protože se pokusíme štětec změnit po jeho zmrazení.

[!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
[!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]

Chcete-li zabránit vyvolání této výjimky, můžete použít <xref:System.Windows.Freezable.IsFrozen%2A> metodu k určení, zda <xref:System.Windows.Freezable> je objekt zmrazen.

[!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
[!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]

V předchozím příkladu kódu byla Upravitelná kopie vytvořena zmrazeným objektem pomocí <xref:System.Windows.Freezable.Clone%2A> metody. Další část popisuje klonování podrobněji.

> [!NOTE]
> Vzhledem k tomu, že zmrazené Freezable nemohou být animovány, systém animace automaticky vytvoří upravitelné klony zmrazených <xref:System.Windows.Freezable> objektů při pokusu o jejich animaci <xref:System.Windows.Media.Animation.Storyboard>pomocí. Chcete-li odstranit režii výkonu způsobenou klonování, ponechte objekt nezmrazený, pokud je v úmyslu ho animovat. Další informace o animování ve scénářích najdete v [přehledu scénářů](../graphics-multimedia/storyboards-overview.md).

### <a name="freezing-from-markup"></a>Zamrznutí ze značek

Chcete-li <xref:System.Windows.Freezable> zablokovat objekt deklarovaný v kódu, `PresentationOptions:Freeze` použijte atribut. V následujícím příkladu <xref:System.Windows.Media.SolidColorBrush> je deklarován jako prostředek stránky a zmrazen. Pak se použije k nastavení pozadí tlačítka.

[!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]

Chcete-li `Freeze` použít atribut, je nutné namapovat na obor názvů možností `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`prezentace:. `PresentationOptions`je doporučená předpona pro mapování tohoto oboru názvů:

```
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"
```

Vzhledem k tomu, že ne všechny čtečky XAML rozpoznávají tento atribut, je doporučeno použít [atribut MC: reignorovat](mc-ignorable-attribute.md) k označení `Presentation:Freeze` atributu jako ignorovatelné:

```
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="PresentationOptions"
```

Další informace najdete na stránce [atributu MC: Reignorovatelné](mc-ignorable-attribute.md) .

### <a name="unfreezing-a-freezable"></a>"Unmrznutí" a Freezable

Po zmrazení <xref:System.Windows.Freezable> nemůže být nikdy upravován ani nezmrazený. můžete však vytvořit nezmrazený klon <xref:System.Windows.Freezable.Clone%2A> pomocí metody nebo <xref:System.Windows.Freezable.CloneCurrentValue%2A> .

V následujícím příkladu je pozadí na tlačítku nastaveno pomocí štětce a následně zmrazení štětce. Nezmrazená kopie se skládá z štětce pomocí <xref:System.Windows.Freezable.Clone%2A> metody. Klon se upraví a použije se ke změně pozadí tlačítka ze žluté na červenou.

[!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
[!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]

> [!NOTE]
> Bez ohledu na to, kterou metodu klonování použijete, se animace nikdy nezkopírují do nového <xref:System.Windows.Freezable>.

Metody <xref:System.Windows.Freezable.Clone%2A> a<xref:System.Windows.Freezable.CloneCurrentValue%2A> vytváří hluboké kopie Freezable. Pokud Freezable obsahuje jiné zmrazené objekty Freezable, naklonují se a dají se upravovat. Například pokud naklonujte zmrazení <xref:System.Windows.Media.PathGeometry> tak, aby bylo možné ho upravovat, hodnoty a segmenty, které obsahuje, jsou také zkopírovány a provedeny jako upravitelné.

<a name="createyourownfreezableclass"></a>

## <a name="creating-your-own-freezable-class"></a>Vytvoření vlastní třídy Freezable

Třída, která je odvozena <xref:System.Windows.Freezable> z, získává následující funkce.

- Speciální stavy: jen pro čtení (zmrazeno) a stav zápisu.

- Bezpečnost vlákna: zmrazení <xref:System.Windows.Freezable> lze sdílet napříč vlákny.

- Podrobné oznámení o změně: Na rozdíl od <xref:System.Windows.DependencyObject>jiných s Freezable objekty poskytují oznámení o změně, když se změní hodnoty dílčích vlastností.

- Snadné klonování: třída Freezable už implementovala několik metod, které vytváří hloubkové klony.

A <xref:System.Windows.Freezable> je <xref:System.Windows.DependencyObject>typu, a proto používá systém vlastností závislosti. Vlastnosti vaší třídy nemusí být vlastnosti závislosti, ale pomocí vlastností závislosti se zmenší množství kódu, který musíte napsat, protože <xref:System.Windows.Freezable> třída byla navržena s vlastnostmi závislosti. Další informace o systému vlastností závislosti naleznete v tématu [Přehled vlastností závislosti](dependency-properties-overview.md).

Každá <xref:System.Windows.Freezable> podtřída musí <xref:System.Windows.Freezable.CreateInstanceCore%2A> přepsat metodu. Pokud vaše třída používá vlastnosti závislosti pro všechna svoje data, budete hotovi.

Pokud vaše třída obsahuje datové členy vlastnosti bez závislosti, je nutné také přepsat následující metody:

- <xref:System.Windows.Freezable.CloneCore%2A>

- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>

- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>

- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>

- <xref:System.Windows.Freezable.FreezeCore%2A>

Také je nutné sledovat následující pravidla pro přístup a zápis do datových členů, kteří nejsou vlastnostmi závislosti:

- Na začátku libovolného rozhraní API, které čte datové členy vlastnosti bez závislosti, zavolejte <xref:System.Windows.Freezable.ReadPreamble%2A> metodu.

- Na začátku jakéhokoli rozhraní API, které zapisuje datové členy vlastnosti bez závislosti, zavolejte <xref:System.Windows.Freezable.WritePreamble%2A> metodu. (Po volání <xref:System.Windows.Freezable.WritePreamble%2A> v rozhraní API není nutné provádět další <xref:System.Windows.Freezable.ReadPreamble%2A> volání, pokud také přečtete datové členy vlastnosti, které nejsou závislé na závislostech.)

- Před ukončením metod, které jsou zapsány do datových členů vlastnosti bez závislosti, volejte metodu.<xref:System.Windows.Freezable.WritePostscript%2A>

Pokud vaše třída obsahuje datové členy, které nejsou <xref:System.Windows.DependencyObject> závislé na vlastnostech, je nutné <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> volat metodu také pokaždé, když změníte jednu z jejich hodnot, a to i v případě, že nastavujete `null`člena.

> [!NOTE]
> Je velmi důležité, abyste začali každou <xref:System.Windows.Freezable> metodu, kterou jste přepsali, voláním základní implementace.

Příklad vlastní <xref:System.Windows.Freezable> třídy naleznete v [ukázce vlastní animace](https://go.microsoft.com/fwlink/?LinkID=159981).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Freezable>
- [Ukázka vlastní animace](https://go.microsoft.com/fwlink/?LinkID=159981)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
