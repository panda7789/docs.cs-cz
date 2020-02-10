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
ms.openlocfilehash: b1887afd19407898d8de1d92252e29778899fb89
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095187"
---
# <a name="freezable-objects-overview"></a>Přehled zablokovatelných objektů

Toto téma popisuje, jak efektivně používat a vytvářet <xref:System.Windows.Freezable> objekty, které poskytují speciální funkce, které mohou pomoci zlepšit výkon aplikace. Příklady objektů Freezable zahrnují štětce, pera, transformace, geometrií a animace.

<a name="whatisafreezable"></a>

## <a name="what-is-a-freezable"></a>Co je Freezable?

<xref:System.Windows.Freezable> je speciální typ objektu, který má dva stavy: nezmrazené a zmrazené. Pokud je nezmrazený, <xref:System.Windows.Freezable> se chová jako jakýkoli jiný objekt. Po zmrazení již <xref:System.Windows.Freezable> nelze upravovat.

<xref:System.Windows.Freezable> poskytuje událost <xref:System.Windows.Freezable.Changed>, která upozorní pozorovatele na jakékoli úpravy objektu. Zmrazení <xref:System.Windows.Freezable> může zlepšit jeho výkon, protože už nepotřebuje věnovat prostředky v oznámeních o změnách. Zmrazený <xref:System.Windows.Freezable> lze také sdílet mezi vlákny, zatímco nezmrazený <xref:System.Windows.Freezable> nemůže.

I když třída <xref:System.Windows.Freezable> má mnoho aplikací, většina <xref:System.Windows.Freezable> objektů v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] souvisí s podsystémem grafiky.

Třída <xref:System.Windows.Freezable> usnadňuje používání určitých grafických systémových objektů a může zvýšit výkon aplikace. Příklady typů, které dědí z <xref:System.Windows.Freezable>, zahrnují třídy <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>a <xref:System.Windows.Media.Geometry>. Vzhledem k tomu, že obsahují nespravované prostředky, systém musí tyto objekty monitorovat pro úpravy a následně aktualizovat odpovídající nespravované prostředky, pokud dojde ke změně původního objektu. I v případě, že ve skutečnosti neupravíte objekt systému grafiky, systém musí stále strávit některé prostředky, které sledují objekt, v případě, že ho změníte.

Předpokládejme například, že vytvoříte <xref:System.Windows.Media.SolidColorBrush> štětce a použijete ho k vykreslování pozadí tlačítka.

[!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
[!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]

Když je toto tlačítko vykresleno, používá dílčí systém [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Graphics informace, které jste zadali k vykreslení skupiny pixelů, aby bylo možné vytvořit vzhled tlačítka. I když jste použili barevný štětec, který popisuje, jak se má tlačítko vykreslit, váš barevný štětec ve skutečnosti neprovede malování. Grafický systém generuje rychlé objekty nízké úrovně pro tlačítko a štětec a jedná se o objekty, které se ve skutečnosti zobrazují na obrazovce.

Pokud jste změnili štětec, bude nutné tyto objekty nízké úrovně znovu vygenerovat. Třída Freezable je to, co umožňuje štětci najít odpovídající vygenerované objekty nízké úrovně a aktualizovat je při změně. Když je tato možnost povolená, bude se štětec považovat za nezmrazený.

<xref:System.Windows.Freezable.Freeze%2A> metoda Freezable vám umožňuje zakázat tuto schopnost automatických aktualizací. Tuto metodu lze použít k tomu, aby se štětec stala "zmrazená", nebo neupravitelný.

> [!NOTE]
> Ne každý objekt Freezable může být zmrazen. Chcete-li zabránit vyvolání <xref:System.InvalidOperationException>, zkontrolujte hodnotu vlastnosti <xref:System.Windows.Freezable.CanFreeze%2A> objektu Freezable a určete, zda může být zmrazena před pokusem o jejich zablokování.

[!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
[!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]

Když už nepotřebujete měnit Freezable, zamrznutí poskytuje výhody pro výkon. Pokud jste v tomto příkladu zablokování štětce, grafický systém už ho nebude potřebovat ke sledování změn. Systém grafiky může také provádět další optimalizace, protože ví, že se štětec nemění.

> [!NOTE]
> Pro usnadnění práce objekty Freezable zůstanou nezmrazené, pokud je explicitně neuvolníte.

<a name="frozenfreezables"></a>

## <a name="using-freezables"></a>Použití Zablokovatelné

Použití nezmrazeného Freezable se podobá použití jiného typu objektu. V následujícím příkladu se barva <xref:System.Windows.Media.SolidColorBrush> změnila ze žluté na červenou, jakmile se použije k vykreslení pozadí tlačítka. Grafický systém funguje na pozadí, aby při příštím obnovení obrazovky automaticky změnil tlačítko od žluté na červenou.

[!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
[!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]

### <a name="freezing-a-freezable"></a>Zmrazení Freezable

Chcete-li nastavit <xref:System.Windows.Freezable> unupravitelný, zavolejte metodu <xref:System.Windows.Freezable.Freeze%2A>. Při zablokování objektu, který obsahuje objekty Freezable, jsou tyto objekty také zmrazeny. Například pokud zadáte <xref:System.Windows.Media.PathGeometry>, hodnoty a segmenty, které obsahuje, by byly zmrazeny.

Freezable **nelze** zmrazit, pokud platí některá z následujících podmínek:

- Obsahuje animované nebo vlastnosti vázaného na data.

- Má vlastnosti nastavené dynamickým prostředkem. (Další informace o dynamických prostředcích najdete v tématu [zdroje XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) .)

- Obsahuje <xref:System.Windows.Freezable> dílčích objektů, které nelze zmrazit.

Pokud jsou tyto podmínky nepravdivé a nechcete <xref:System.Windows.Freezable>upravovat, měli byste je zmrazit, abyste získali výše popsané výhody výkonu.

Jakmile zavoláte metodu <xref:System.Windows.Freezable.Freeze%2A> Freezable, už ji nebude možné upravovat. Při pokusu o úpravu zmrazeného objektu dojde k vyjímka <xref:System.InvalidOperationException>. Následující kód vyvolá výjimku, protože se pokusíme štětec změnit po jeho zmrazení.

[!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
[!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]

Chcete-li zabránit vyvolání této výjimky, můžete použít metodu <xref:System.Windows.Freezable.IsFrozen%2A> k určení, zda je <xref:System.Windows.Freezable> zmrazen.

[!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
[!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]

V předchozím příkladu kódu bylo provedeno upravitelné kopírování zmrazeného objektu pomocí metody <xref:System.Windows.Freezable.Clone%2A>. Další část popisuje klonování podrobněji.

> [!NOTE]
> Vzhledem k tomu, že zmrazené Freezable nemohou být animovány, systém animace automaticky vytvoří upravitelné klony zmrazených objektů <xref:System.Windows.Freezable> při pokusu o jejich animaci pomocí <xref:System.Windows.Media.Animation.Storyboard>. Chcete-li odstranit režii výkonu způsobenou klonování, ponechte objekt nezmrazený, pokud je v úmyslu ho animovat. Další informace o animování ve scénářích najdete v [přehledu scénářů](../graphics-multimedia/storyboards-overview.md).

### <a name="freezing-from-markup"></a>Zamrznutí ze značek

Chcete-li zablokovat objekt <xref:System.Windows.Freezable> deklarovaný v kódu, použijte atribut `PresentationOptions:Freeze`. V následujícím příkladu je <xref:System.Windows.Media.SolidColorBrush> deklarován jako prostředek stránky a zmrazen. Pak se použije k nastavení pozadí tlačítka.

[!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]

Chcete-li použít atribut `Freeze`, je nutné namapovat na obor názvů možností prezentace: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. `PresentationOptions` je doporučená předpona pro mapování tohoto oboru názvů:

```xaml
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"
```

Vzhledem k tomu, že ne všechny čtečky XAML rozpoznávají tento atribut, doporučuje se použít [atribut MC: ignorovat](mc-ignorable-attribute.md) k označení atributu `Presentation:Freeze` jako ignorovatelné:

```xaml
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="PresentationOptions"
```

Další informace najdete na stránce [atributu MC: Reignorovatelné](mc-ignorable-attribute.md) .

### <a name="unfreezing-a-freezable"></a>"Unmrznutí" a Freezable

Po zmrazení <xref:System.Windows.Freezable> nemůže být nikdy upravována nebo nezmrazena; Můžete ale vytvořit nezmrazený klon pomocí metody <xref:System.Windows.Freezable.Clone%2A> nebo <xref:System.Windows.Freezable.CloneCurrentValue%2A>.

V následujícím příkladu je pozadí na tlačítku nastaveno pomocí štětce a následně zmrazení štětce. Nezmrazená kopie se skládá z štětce pomocí metody <xref:System.Windows.Freezable.Clone%2A>. Klon se upraví a použije se ke změně pozadí tlačítka ze žluté na červenou.

[!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
[!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]

> [!NOTE]
> Bez ohledu na to, kterou metodu klonování použijete, se animace nikdy nezkopírují do nového <xref:System.Windows.Freezable>.

Metody <xref:System.Windows.Freezable.Clone%2A> a <xref:System.Windows.Freezable.CloneCurrentValue%2A> vytváří hluboké kopie Freezable. Pokud Freezable obsahuje jiné zmrazené objekty Freezable, naklonují se a dají se upravovat. Pokud například naklonete zmrazené <xref:System.Windows.Media.PathGeometry> tak, aby bylo možné je upravovat, hodnoty a segmenty, které obsahuje, jsou také zkopírovány a provedeny jako upravitelné.

<a name="createyourownfreezableclass"></a>

## <a name="creating-your-own-freezable-class"></a>Vytvoření vlastní třídy Freezable

Třída odvozená z <xref:System.Windows.Freezable> získává následující funkce.

- Speciální stavy: jen pro čtení (zmrazeno) a stav zápisu.

- Bezpečnost vlákna: zmrazený <xref:System.Windows.Freezable> lze sdílet napříč vlákny.

- Podrobné oznámení o změně: na rozdíl od jiných <xref:System.Windows.DependencyObject>s objekty Freezable poskytují oznámení o změně, když se změní hodnoty dílčích vlastností.

- Snadné klonování: třída Freezable už implementovala několik metod, které vytváří hloubkové klony.

<xref:System.Windows.Freezable> je typ <xref:System.Windows.DependencyObject>a proto používá systém vlastností závislosti. Vlastnosti vaší třídy nemusí být vlastnosti závislostí, ale pomocí vlastností závislosti se zmenší množství kódu, který musíte napsat, protože třída <xref:System.Windows.Freezable> byla navržena s ohledem na vlastnosti závislosti. Další informace o systému vlastností závislosti naleznete v tématu [Přehled vlastností závislosti](dependency-properties-overview.md).

Každá podtřída <xref:System.Windows.Freezable> musí přepsat metodu <xref:System.Windows.Freezable.CreateInstanceCore%2A>. Pokud vaše třída používá vlastnosti závislosti pro všechna svoje data, budete hotovi.

Pokud vaše třída obsahuje datové členy vlastnosti bez závislosti, je nutné také přepsat následující metody:

- <xref:System.Windows.Freezable.CloneCore%2A>

- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>

- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>

- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>

- <xref:System.Windows.Freezable.FreezeCore%2A>

Také je nutné sledovat následující pravidla pro přístup a zápis do datových členů, kteří nejsou vlastnostmi závislosti:

- Na začátku libovolného rozhraní API, které čte datové členy vlastnosti bez závislosti, zavolejte metodu <xref:System.Windows.Freezable.ReadPreamble%2A>.

- Na začátku jakéhokoli rozhraní API, které zapisuje datové členy vlastnosti bez závislosti, zavolejte metodu <xref:System.Windows.Freezable.WritePreamble%2A>. (Po zavolání <xref:System.Windows.Freezable.WritePreamble%2A> v rozhraní API není nutné provádět další volání <xref:System.Windows.Freezable.ReadPreamble%2A>, pokud také přečtete datové členy vlastnosti bez závislosti.)

- Před ukončením metod, které jsou zapsány do datových členů vlastnosti bez závislosti, volejte metodu <xref:System.Windows.Freezable.WritePostscript%2A>.

Pokud vaše třída obsahuje datové členy, které nejsou závislé na vlastnostech, které jsou <xref:System.Windows.DependencyObject> objekty, je nutné zavolat <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> metodu pokaždé, když změníte jednu z jejich hodnot, i když nastavíte člena na `null`.

> [!NOTE]
> Je velmi důležité, abyste začali každou metodu <xref:System.Windows.Freezable>, kterou přepíšete voláním základní implementace.

Příklad vlastní třídy <xref:System.Windows.Freezable> naleznete v [ukázce vlastní animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Freezable>
- [Ukázka vlastní animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
