---
title: "Přehled zablokovatelných objektů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 49778dc9551652ee4a4d36426b4b396652b9dcd2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="freezable-objects-overview"></a>Přehled zablokovatelných objektů
Toto téma popisuje, jak efektivně používat a vytvořit <xref:System.Windows.Freezable> objekty, které poskytují zvláštní funkce, které může pomoct zlepšit výkon aplikace. Příklady zmrazitelné objekty: štětce, pera, transformace, geometrie a animace.  
  
<a name="whatisafreezable"></a>   
## <a name="what-is-a-freezable"></a>Co je zmrazitelné?  
 A <xref:System.Windows.Freezable> je zvláštní typ objektu, který má dva stavy: zmrazen a pozastaveny. Když nefixované, <xref:System.Windows.Freezable> se chovají jako jakýkoliv jiný objekt. Když pozastaveny, <xref:System.Windows.Freezable> již nebude možné upravit.  
  
 A <xref:System.Windows.Freezable> poskytuje <xref:System.Windows.Freezable.Changed> události pro upozornění pozorovatelů veškeré úpravy objektu. Zmrazení <xref:System.Windows.Freezable> může zvýšit jeho výkon, protože už je nutné vynaložit prostředky na oznámení o změnách. Ukotvené <xref:System.Windows.Freezable> také sdílet napříč vlákny, při nefixované <xref:System.Windows.Freezable> nelze.  
  
 I když <xref:System.Windows.Freezable> třída má mnoho aplikací nejvíce <xref:System.Windows.Freezable> objekty v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se vztahují k grafiky dílčí systému.  
  
 <xref:System.Windows.Freezable> Třídy je jednodušší použít určité grafických objektů systému a může pomoct zlepšit výkon aplikace. Příklady typů, které dědí od <xref:System.Windows.Freezable> zahrnují <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>, a <xref:System.Windows.Media.Geometry> třídy. Protože obsahují nespravovaných prostředků, musíte systému monitorování tyto objekty pro úpravy a aktualizujte jejich odpovídající nespravovaných prostředků, když dojde ke změně původní objekt. I v případě, že nebudete muset měnit ve skutečnosti systémový objekt grafiky, systém musí stále tráví některé jeho prostředky objekt, monitorování v případě, že ho změnit.  
  
 Předpokládejme například, že vytvoříte <xref:System.Windows.Media.SolidColorBrush> zdokonalit a použít ho k vyplnění pozadí tlačítko.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 Když se zobrazí tlačítko [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafiky dílčí systém využívá informace, které jste zadali pro malování skupinu pixelů k vytvoření vzhled tlačítka. I když jste použili plnobarevné štětce k popisu, jak by měla být tlačítko vykresluje, vaše plnobarevné štětce neprovádí ve skutečnosti Malování. Grafika systému generuje rychlé, nízké úrovně objekty pro tlačítko a stopy a ty objekty, které ve skutečnosti se zobrazují na obrazovce.  
  
 Pokud byste chtěli upravit štětec, tyto objekty nízké úrovně by musel znovu vygeneruje. Zmrazitelné třída je dává štětce umožňuje najít odpovídající vygenerovaný, nízké úrovně objekty a provede jejich aktualizaci při změně. Pokud je tato možnost povolena, stopy říká, že je jako "nefixované."  
  
 Zmrazitelné na <xref:System.Windows.Freezable.Freeze%2A> metoda umožňuje zakázat tato schopnost automatických aktualizací. Tuto metodu můžete použít k vytvoření štětce stane "ukotvené", nebo unmodifiable.  
  
> [!NOTE]
>  Ne každý objekt zmrazitelné lze ukotvit. Aby se zabránilo vyvolání <xref:System.InvalidOperationException>, zkontrolujte hodnotu zmrazitelné objektu <xref:System.Windows.Freezable.CanFreeze%2A> vlastnosti k určení, zda lze ukotvit před pokusem o ho zastavit.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 Pokud již nepotřebujete upravit zmrazitelné, zmrazení ho poskytuje výhody výkonu. Pokud byste chtěli zmrazení štětce v tomto příkladu, grafika systému by už nemusíte sledovat změny. Grafika systému lze také nastavit další optimalizace, protože bude vědět, že nedojde ke změně stopy.  
  
> [!NOTE]
>  Pro usnadnění práce zůstanou nefixované zmrazitelné objekty, dokud je explicitně ukotvit.  
  
<a name="frozenfreezables"></a>   
## <a name="using-freezables"></a>Pomocí Freezables  
 Použití nefixované zmrazitelné je jako jiný typ objektu. V následujícím příkladu, barvu <xref:System.Windows.Media.SolidColorBrush> se změní z žlutý na red po je použita k vyplnění pozadí tlačítko. Grafika systému funguje na pozadí a automaticky změní na tlačítko z žlutý red při příští aktualizaci na obrazovce.  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### <a name="freezing-a-freezable"></a>Zmrazení zmrazitelné  
 Chcete-li <xref:System.Windows.Freezable> zavoláte unmodifiable, jeho <xref:System.Windows.Freezable.Freeze%2A> metoda. Po ukotvení objekt, který obsahuje zmrazitelné objekty se tyto objekty jsou také pozastaveny. Například, pokud ukotvení <xref:System.Windows.Media.PathGeometry>, obrázky a segmentů obsahuje by pozastaveny příliš.  
  
 Freezable **nelze** pozastaveny, pokud platí některá z následujících akcí:  
  
-   Má animovaný nebo data vázané vlastnosti.  
  
-   Obsahuje vlastnosti nastavit dynamické prostředek. (Najdete v článku [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md) Další informace o dynamické prostředky.)  
  
-   Obsahuje <xref:System.Windows.Freezable> dílčí objekty, které nelze ukotvit.  
  
 Pokud tyto podmínky se false a nemáte v úmyslu změnit <xref:System.Windows.Freezable>, pak by ho získat výhody výkonu dříve popisované zastavit.  
  
 Jakmile zavoláte zmrazitelné na <xref:System.Windows.Freezable.Freeze%2A> metodu, můžete již změnit. Pokusu o změnu ukotvené objektu příčiny <xref:System.InvalidOperationException> vyvolání. Následující kód vyvolá výjimku, protože jsme pokusí změnit stopy po byly pozastaveny.  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 Abyste se vyhnuli vyvolání výjimku, můžete použít <xref:System.Windows.Freezable.IsFrozen%2A> metoda k určení zda <xref:System.Windows.Freezable> nereaguje.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 V předchozím příkladu kód byl proveden kopii upravitelnými ukotvené objekt pomocí <xref:System.Windows.Freezable.Clone%2A> metoda. Další část popisuje podrobněji klonování.  
  
 **Poznámka:** protože ukotvené zmrazitelné nemůže být animovaný, systém animace automaticky vytvoří upravitelnými klony z ukotvené <xref:System.Windows.Freezable> objekty při pokusu o jejich s animace <xref:System.Windows.Media.Animation.Storyboard>. Omezit výkon režie způsobené klonování, ponechte objekt nefixované, pokud máte v úmyslu ho animace. Další informace o animaci s scénářů najdete v tématu [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
### <a name="freezing-from-markup"></a>Zmrazení z kódu  
 Chcete-li ukotvit <xref:System.Windows.Freezable> objekt definována v značek, je `PresentationOptions:Freeze` atribut. V následujícím příkladu <xref:System.Windows.Media.SolidColorBrush> je deklarován jako prostředek stránky a pozastaveny. Pak slouží k nastavení pozadí tlačítko.  
  
 [!code-xaml[FreezableSample#FreezeFromMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 Použít `Freeze` atributu, je nutné mapovat do oboru názvů možnosti prezentace: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. `PresentationOptions`je předpona doporučené pro mapování tento obor názvů:  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 Protože ne všechny čtečky XAML rozpoznat tento atribut, je doporučeno používat [mc: Ignorovatelná atribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) označit `Presentation:Freeze` atribut jako Ignorovatelná:  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 Další informace najdete v tématu [mc: Ignorovatelná atribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) stránky.  
  
### <a name="unfreezing-a-freezable"></a>"Unfreezing" zmrazitelné  
 Jednou pozastaveny, <xref:System.Windows.Freezable> nelze změnit ani nefixované; však můžete vytvořit nefixované klon pomocí <xref:System.Windows.Freezable.Clone%2A> nebo <xref:System.Windows.Freezable.CloneCurrentValue%2A> metoda.  
  
 V následujícím příkladu pozadí na tlačítko nastavena štětcem a pak tento stopy nereaguje. Nefixované kopírování se provádí pomocí štětce <xref:System.Windows.Freezable.Clone%2A> metoda. Klon je upravit a použít ke změně pozadí na tlačítko z žlutý na červený.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  Bez ohledu na to, které můžete použít metodu klonování, animace se nikdy zkopírují do nových <xref:System.Windows.Freezable>.  
  
 <xref:System.Windows.Freezable.Clone%2A> a <xref:System.Windows.Freezable.CloneCurrentValue%2A> metody vracet hloubkové kopií zmrazitelné. Pokud zmrazitelné obsahuje jiné pozastaveny zmrazitelné objekty, jsou také klonovat a provedených změn. Například, pokud jste klonovat ukotvené <xref:System.Windows.Media.PathGeometry> umožníte provádění změn, obrázky a segmentů obsahuje také zkopírovány a provedených změn.  
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a>Vytvoření vlastního zmrazitelné – třída  
 Třída odvozená z <xref:System.Windows.Freezable> získá následující funkce.  
  
-   Speciální stavů: jen pro čtení (pozastaveny) a stavu pro zápis.  
  
-   Bezpečnost vlákna: ukotvené <xref:System.Windows.Freezable> mohlo sdílet víc vláken.  
  
-   Podrobné oznámení o změně: na rozdíl od jiných <xref:System.Windows.DependencyObject>s, zmrazitelné objekty poskytnout oznámení o změnách při změně hodnoty dílčí vlastnosti.  
  
-   Snadno klonování: zmrazitelné třídy již implementovala několik metod, které produkují hloubkové klonovat.  
  
 A <xref:System.Windows.Freezable> je typ <xref:System.Windows.DependencyObject>a proto používá systém vlastnost závislosti. Vlastnosti vaší třídy nemají být vlastností závislostí, ale pomocí vlastností závislostí se sníží množství kódu, budete muset zapisovat, protože <xref:System.Windows.Freezable> třída byl navržen s vlastností závislostí v paměti. Další informace o systému vlastnost závislosti najdete v tématu [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 Každý <xref:System.Windows.Freezable> podtřídami musí přepsat <xref:System.Windows.Freezable.CreateInstanceCore%2A> metoda. Pokud třídu vlastností závislostí používá pro všechna její data, budete hotovi.  
  
 Pokud vaše třída obsahuje vlastnost bez závislostí datové členy, je nutné přepsat následující metody:  
  
-   <xref:System.Windows.Freezable.CloneCore%2A>  
  
-   <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
-   <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 Také musí odpovídat následujícím pravidlům pro přístup k informacím a zápis do datových členů, které nejsou vlastnosti závislosti:  
  
-   Na začátku každého [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] , který čte vlastnost bez závislostí datových členů, volejte <xref:System.Windows.Freezable.ReadPreamble%2A> metoda.  
  
-   Na začátku jakéhokoli rozhraní API, která zapisuje vlastnost bez závislostí datových členů, volání <xref:System.Windows.Freezable.WritePreamble%2A> metoda. (Po jste jste volali metodu <xref:System.Windows.Freezable.WritePreamble%2A> v [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], není nutné provést další volání do <xref:System.Windows.Freezable.ReadPreamble%2A> Pokud si také přečíst vlastnost bez závislostí datových členů.)  
  
-   Volání <xref:System.Windows.Freezable.WritePostscript%2A> metoda před ukončením metody, které zapsat do vlastnosti bez závislosti datových členů.  
  
 Pokud vaše třída obsahuje závislost vlastnost datových členů, které jsou <xref:System.Windows.DependencyObject> objekty, musíte také zavolat <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> metoda při každé změně na jejich hodnot, i když jste nastavení člena na `null`.  
  
> [!NOTE]
>  To je velmi důležité, každý začnete <xref:System.Windows.Freezable> metoda přepsat pomocí volání základní implementaci.  
  
 Příklad vlastní <xref:System.Windows.Freezable> naleznete [vlastní animace ukázka](http://go.microsoft.com/fwlink/?LinkID=159981).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Freezable>  
 [Ukázka vlastní animace](http://go.microsoft.com/fwlink/?LinkID=159981)  
 [Přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Vlastnosti vlastní závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
