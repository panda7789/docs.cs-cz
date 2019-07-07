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
ms.openlocfilehash: 79c539bd0117c712670601b7498c490fca76090e
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610523"
---
# <a name="freezable-objects-overview"></a>Přehled zablokovatelných objektů
Toto téma popisuje, jak efektivně používat a vytvořte <xref:System.Windows.Freezable> objekty, které mají speciální funkcí, které může pomoct zlepšit výkon aplikace. Příklady zablokovatelných objektů: štětce, pera, transformace, geometrie a animace.  
  
<a name="whatisafreezable"></a>   
## <a name="what-is-a-freezable"></a>Co je zablokovatelného objektu?  
 A <xref:System.Windows.Freezable> je speciální typ objektu, který má dva stavy: zmrazen a je zmrazen. Když zmrazen, <xref:System.Windows.Freezable> se chovají stejně jako jakýkoli jiný objekt. Když zmrazeno, <xref:System.Windows.Freezable> už je možné upravit.  
  
 A <xref:System.Windows.Freezable> poskytuje <xref:System.Windows.Freezable.Changed> událost oznámení pozorovatele veškeré úpravy objektu. Zmrazení <xref:System.Windows.Freezable> můžete vylepšit výkon, protože už nebude potřeba utratit za prostředky oznámení o změnách. Zmrazený <xref:System.Windows.Freezable> se dají sdílet taky přes více vláken při nezmrazený <xref:System.Windows.Freezable> nelze.  
  
 I když <xref:System.Windows.Freezable> třída má mnoho aplikací, většina <xref:System.Windows.Freezable> objekty v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se vztahují k grafiky subsystémů.  
  
 <xref:System.Windows.Freezable> Třída usnadňuje použití určitých systémových objektů grafiky a může pomoct zlepšit výkon aplikace. Příklady typů, které dědí z <xref:System.Windows.Freezable> zahrnout <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>, a <xref:System.Windows.Media.Geometry> třídy. Protože obsahují nespravované prostředky, musí systém monitorovat tyto objekty pro úpravy a pak aktualizujte jejich odpovídající nespravované prostředky, když dojde ke změně na původní objekt. I v případě, že nebudete muset měnit skutečně systémový objekt grafiky, systém musíte stále věnovat některé z jejích prostředků objekt monitorování v případě, že ho změnit.  
  
 Předpokládejme například, že vytvoříte <xref:System.Windows.Media.SolidColorBrush> štětce a použít ho k vykreslení na pozadí tlačítka.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 Při vykreslování na tlačítko [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafiky subsystémů používá údaje vykreslení skupiny obrazových bodů pro vytvoření vzhledu tlačítka. I když jste použili štětec jednotné barvy popisující, jak by měl překreslit tlačítko, vaše štětec jednotné barvy neumí skutečně Malování. Grafika systému generuje rychlé, nízké úrovně objektů pro tlačítko a štětce a ty objekty, které ve skutečnosti se zobrazí na obrazovce.  
  
 Pokud byste chtěli upravit štětec, těchto objektů nízké úrovně musel být znovu vygenerován. Freezable – třída je, co umožňuje štětce a najít odpovídající objekty vygenerovaný, nízké úrovně, aktualizovat je, když se změní. Pokud je tato možnost povolena, štětec je označen jako "nezmrazený."  
  
 Zablokovatelného objektu <xref:System.Windows.Freezable.Freeze%2A> metoda umožňuje zakázat automatických aktualizací. Aby štětce stane "zmrazená" nebo neupravitelných můžete použít tuto metodu.  
  
> [!NOTE]
>  Ne každá Zmrazitelný objekt lze ukotvit. Aby se zabránilo vyvolání <xref:System.InvalidOperationException>, zkontrolujte hodnotu Zmrazitelný objekt <xref:System.Windows.Freezable.CanFreeze%2A> a určí, zda lze ukotvit před pokusem o ho zastavit.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 Pokud už nepotřebujete změnit zablokovatelného objektu, zamrzá ji poskytuje výhody výkonu. Pokud byste chtěli ukotvit štětce v tomto příkladu, systém grafiky by už nemusíte sledovat změny. Grafika systému lze také nastavit další optimalizace, protože ví, že nedojde ke změně stopy.  
  
> [!NOTE]
>  Pro usnadnění práce zůstanou nezmrazený zablokovatelných objektů, pokud explicitně zmrazit je.  
  
<a name="frozenfreezables"></a>   
## <a name="using-freezables"></a>Pomocí Zablokovatelné  
 Pomocí nezmrazený zablokovatelného objektu je jako použití jakéhokoli jiného typu objektu. V následujícím příkladu, barvu <xref:System.Windows.Media.SolidColorBrush> změněn z žlutá červená po slouží k vykreslení na pozadí tlačítka. Grafika systému funguje na pozadí automaticky změnit na tlačítko z žlutá červená při příštím spuštění se aktualizují na obrazovce.  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### <a name="freezing-a-freezable"></a>Zmrazení zablokovatelného objektu  
 Chcete-li <xref:System.Windows.Freezable> zavoláte neupravitelných, jeho <xref:System.Windows.Freezable.Freeze%2A> metoda. Po ukotvení objekt, který obsahuje zablokovatelných objektů jsou tyto objekty také zmražená. Například, pokud ukotvení <xref:System.Windows.Media.PathGeometry>, obrázky a segmentů obsahuje by zmrazené příliš.  
  
 Freezable **nelze** zmrazit, pokud je splněna některá z následujících akcí:  
  
- Má animovat nebo data vázané vlastnosti.  
  
- Obsahuje vlastnosti nastavit pomocí dynamického prostředku. (Najdete v článku [prostředky XAML](xaml-resources.md) Další informace o dynamické prostředků.)  
  
- Obsahuje <xref:System.Windows.Freezable> podřízených objektů, které nelze zmrazit.  
  
 Pokud jsou tyto podmínky hodnotu false a nemáte v úmyslu změnit <xref:System.Windows.Freezable>, pak by měl ukotvit to zlepší výkon popsané výše.  
  
 Po volání zablokovatelného objektu <xref:System.Windows.Freezable.Freeze%2A> metoda, je již upravit. Pokouší změnit zmrazený objektu způsobí, že <xref:System.InvalidOperationException> vyvolání. Následující kód vyvolá výjimku, protože jsme pokusí změnit stopy po je zmrazen.  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 Abyste se vyhnuli vyvolání této výjimky, můžete použít <xref:System.Windows.Freezable.IsFrozen%2A> metodou ke zjištění, zda <xref:System.Windows.Freezable> je zmrazen.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 V předchozím příkladu kódu byla provedena zmrazených objektů pomocí kopii lze měnit <xref:System.Windows.Freezable.Clone%2A> metody. Další část pojednává o klonování podrobněji.  
  
 **Poznámka:** protože zmrazený zablokovatelného objektu nelze animovat, systém animace automaticky vytvoří upravitelné klony z zmrazené <xref:System.Windows.Freezable> objekty při pokusu o jejich animace <xref:System.Windows.Media.Animation.Storyboard>. Eliminuje režie naklonováním způsobeno výkon, ponechte objekt zmrazen, pokud máte v úmyslu jej lze animovat. Další informace o animace s použitím scénářů, najdete v článku [přehled scénářů](../graphics-multimedia/storyboards-overview.md).  
  
### <a name="freezing-from-markup"></a>Zastaveno z kódu  
 Zablokovat a nešlo <xref:System.Windows.Freezable> objekt deklarován v kódu, je použít `PresentationOptions:Freeze` atribut. V následujícím příkladu <xref:System.Windows.Media.SolidColorBrush> je deklarován jako prostředek stránky a je zmrazen. Potom slouží k nastavení pozadí tlačítka.  
  
 [!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 Použít `Freeze` atribut, je nutné mapovat do oboru názvů možnosti prezentace: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. `PresentationOptions` je doporučené předpona pro mapování tento obor názvů:  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 Protože ne všechny čtenáři XAML rozpoznat tento atribut, doporučuje se, že používáte [mc: ignorable – atribut](mc-ignorable-attribute.md) k označení `Presentation:Freeze` jako ignorable – atribut:  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 Další informace najdete v tématu [mc: ignorable – atribut](mc-ignorable-attribute.md) stránky.  
  
### <a name="unfreezing-a-freezable"></a>"Unfreezing" zablokovatelného objektu  
 Zmrazené jednou, <xref:System.Windows.Freezable> nelze změnit ani zmrazen; však můžete vytvořit nezmrazený klon pomocí <xref:System.Windows.Freezable.Clone%2A> nebo <xref:System.Windows.Freezable.CloneCurrentValue%2A> metody.  
  
 V následujícím příkladu pozadí tlačítka se nastaví pomocí štětce a tento štětce pak je zmrazen. Nezmrazený kopírování je tvořen pomocí štětce <xref:System.Windows.Freezable.Clone%2A> metody. Klonování je změnit a použít ke změně pozadí tlačítka z žlutá červená.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  Bez ohledu na to, které můžete použít metodu klonování, animací nikdy zkopírovány do nového <xref:System.Windows.Freezable>.  
  
 <xref:System.Windows.Freezable.Clone%2A> a <xref:System.Windows.Freezable.CloneCurrentValue%2A> metody vracet hluboká kopie zablokovatelného objektu. Pokud zablokovatelného objektu obsahuje další zmrazené zablokovatelných objektů, jsou také klonovat a provedli lze měnit. Například, pokud se klonování zmrazený <xref:System.Windows.Media.PathGeometry> , aby upravitelná, obrázky a segmentů obsahuje jsou také zkopírovali a provedli lze měnit.  
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a>Vytváření vlastních freezable – třída  
 Třída, která je odvozena z <xref:System.Windows.Freezable> získá následující funkce.  
  
- Speciální stavy: jen pro čtení (zmrazeno) a stavu pro zápis.  
  
- Bezpečnost vlákna: zmrazený <xref:System.Windows.Freezable> mohou být sdílena mezi vlákny.  
  
- Oznámení o změně podrobné: Na rozdíl od jiných <xref:System.Windows.DependencyObject>s, Zablokovatelných objektů poskytují oznámení o změnách při změně hodnoty vlastnosti dílčí.  
  
- Snadné klonování: zablokovatelného objektu třídy již provedlo několik metod, které vytvářejí hloubkové duplicity.  
  
 A <xref:System.Windows.Freezable> je typ <xref:System.Windows.DependencyObject>a proto používá systém vlastnost závislosti. Vlastnosti vaší třídy nemusí být vlastnosti závislostí, ale pomocí vlastnosti závislosti se sníží množství kódu, je nutné zapsat, protože <xref:System.Windows.Freezable> třídy byla navržena s vlastností závislosti v úvahu. Další informace o systému vlastnost závislosti, najdete v článku [přehled vlastností závislosti](dependency-properties-overview.md).  
  
 Každý <xref:System.Windows.Freezable> podtřídy musí přepsat <xref:System.Windows.Freezable.CreateInstanceCore%2A> metody. Pokud vaše třída používá vlastnosti závislosti pro všechna jeho data, jste hotovi.  
  
 Pokud vaše třída obsahuje vlastnosti bez závislosti datových členů, musí také přepsat následující metody:  
  
- <xref:System.Windows.Freezable.CloneCore%2A>  
  
- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
- <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 Také musí odpovídat následujícím pravidlům pro přístup k a zápis do datových členů, které nejsou vlastnosti závislosti:  
  
- Na začátku žádné [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] , který čte vlastnost bez závislosti datové členy, zavolejte <xref:System.Windows.Freezable.ReadPreamble%2A> metody.  
  
- Na začátku jakéhokoli rozhraní API, která zapisuje vlastnost bez závislosti datové členy, zavolejte <xref:System.Windows.Freezable.WritePreamble%2A> metody. (Když jste volat <xref:System.Windows.Freezable.WritePreamble%2A> v rozhraní API, není nutné provést další volání do <xref:System.Windows.Freezable.ReadPreamble%2A> Pokud načtete vlastnost bez závislosti datové členy.)  
  
- Volání <xref:System.Windows.Freezable.WritePostscript%2A> metoda před ukončením metody, které se zápis do vlastnosti bez závislosti datové členy.  
  
 Pokud vaše třída obsahuje závislost vlastnost datové členy, které jsou <xref:System.Windows.DependencyObject> objekty, musíte také zavolat <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> metoda pokaždé, když změníte obsah některého z jejich hodnot, i v případě, že nastavujete člen `null`.  
  
> [!NOTE]
>  Je velmi důležité, že začnete každý <xref:System.Windows.Freezable> přepsat pomocí volání základní implementaci metody.  
  
 Příklad vlastní <xref:System.Windows.Freezable> najdete v tématu [animace ukázková](https://go.microsoft.com/fwlink/?LinkID=159981).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Freezable>
- [Ukázka vlastních animací](https://go.microsoft.com/fwlink/?LinkID=159981)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
