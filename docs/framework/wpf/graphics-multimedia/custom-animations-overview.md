---
title: Přehled vlastních animací
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes [WPF], animation
- key frames [WPF], custom
- custom key frames [WPF]
- animation [WPF], custom classes
- custom animation classes [WPF]
ms.assetid: 9be69d50-3384-4938-886f-08ce00e4a7a6
ms.openlocfilehash: a18898f340c68b7890c56b586c87870c50fd4686
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131413"
---
# <a name="custom-animations-overview"></a>Přehled vlastních animací
Toto téma popisuje, jak a kdy k rozšíření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace systém tak, že vytvoříte vlastní klíčové snímky animace třídy, nebo pomocí zpětného volání za rámce se.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu informace o tom, měli byste se seznámit s různými typy animací poskytované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Další informace najdete v tématu Přehled animací From/To/By, [přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)a [přehled animací cesty](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md).  
  
 Protože animace třídy dědí <xref:System.Windows.Freezable> třídy, měli byste se seznámit s <xref:System.Windows.Freezable> objekty a o tom, jak dědit z <xref:System.Windows.Freezable>. Další informace najdete v tématu [přehled Zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>Rozšíření systému animace  
 Existuje několik způsobů, jak rozšířit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace systému, v závislosti na úrovni integrované funkce, kterou chcete použít.  Existují tři primární rozšiřitelnost body v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace modul:  
  
-   Vytvoření vlastní klíčové rámečku objektu děděním z jednoho z  *\<typ >* klíčový snímek třídy, jako například <xref:System.Windows.Media.Animation.DoubleKeyFrame>. Tento přístup používá většina vestavěnou funkci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modul animace.  
  
-   Vytvoření vlastní třídy animace děděním z <xref:System.Windows.Media.Animation.AnimationTimeline> nebo jeden z  *\<typ >* AnimationBase třídy.  
  
-   Generovat animací na základě podle snímků pomocí zpětné volání na snímku. Tento přístup se zcela vynechá animace a časování systému.  
  
 Následující tabulka popisuje některé scénáře pro rozšíření systému animace.  
  
|Pokud chcete...|Tuto metodu použijte|  
|-------------------------|-----------------------|  
|Přizpůsobení interpolaci mezi hodnotami typu, který má odpovídající  *\<typ >* AnimationUsingKeyFrames|Vytvořte vlastní klíčové rámečku. Další informace najdete v tématu [vytvořit objekt Frame vlastní klíč](#createacustomkeyframe) oddílu.|  
|Přizpůsobení víc než jenom interpolaci mezi hodnotami typu, který má odpovídající  *\<typ >* animace.|Vytvořte vlastní animace třídu, která dědí z  *\<typ >* AnimationBase třídu, která odpovídá typu, který má být animován. Další informace najdete v tématu [vytvoření vlastní třídy animace](#createacustomanimationtype) oddílu.|  
|Animace typ, který nemá odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace|Použití <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> nebo vytvořit třídu, která dědí z <xref:System.Windows.Media.Animation.AnimationTimeline>. Další informace najdete v tématu [vytvoření vlastní třídy animace](#createacustomanimationtype) oddílu.|  
|Animovat více objektů s hodnotami, které se počítají každá snímků a jsou založeny na poslední sadu interakce s objekty|Použijte na rámce zpětného volání. Další informace najdete v tématu [vytvořte zpětné volání na rámec použití](#useperframecallback) oddílu.|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>Vytvořit vlastní klíčové rámečku  
 Vytvoření vlastní klíčové rámečku třídy je nejjednodušší způsob, jak rozšířit systém animace. Tuto metodu použijte, pokud chcete metodu různých interpolace animace klíčových snímků.  Jak je popsáno v [přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md), animace klíčových snímků používá ke generování jeho výstupní hodnoty klíčových snímků objektů. Každý objekt klíčový snímek provádí tři funkce:  
  
-   Určuje cílový hodnotu pomocí jeho <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> vlastnost.  
  
-   Určuje dobu, kdy by mělo být tato hodnota dosaženo pomocí jeho <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> vlastnost.  
  
-   Interpolaci hodnotu předchozí klíčový snímek a vlastní hodnotu implementací metody InterpolateValueCore.  
  
 **Pokyny k implementaci**  
  
 Odvozovat  *\<typ >* klíčový snímek abstraktní třídy a implementovat metodu InterpolateValueCore. Metoda InterpolateValueCore vrátí aktuální hodnotu klíčového snímku. Přebírá dva parametry: hodnoty předchozí klíčový snímek a průběh hodnotu od 0 do 1. Průběh 0 označuje klíčový snímek byl spuštěn, a hodnota 1 označuje, že klíčový snímek dokončil a by měl vrátit hodnotu zadanou pomocí jeho <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> vlastnost.  
  
 Protože  *\<typ >* klíčový snímek třídy dědí z <xref:System.Windows.Freezable> třídy, je nutné také přepsat <xref:System.Windows.Freezable.CreateInstanceCore%2A> core vrací novou instanci třídy. Pokud třída nepoužívá vlastnosti závislosti k ukládání svých dat nebo vyžaduje dodatečnou inicializaci. po jeho vytvoření, možná budete muset přepsat další metody; Zobrazit [přehled Zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) Další informace.  
  
 Po vytvoření vlastních  *\<typ >* klíčový snímek animace, můžete ji  *\<typ >* AnimationUsingKeyFrames pro daný typ.  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>Vytvořte třídu vlastní animace  
 Vytváří se vlastní animace typ získáte tak větší kontrolu nad tím, jak animovat objektu v. Existují dva doporučené způsoby, jak vytvořit vlastní typ animace: lze odvodit z <xref:System.Windows.Media.Animation.AnimationTimeline> třídy nebo  *\<typ >* AnimationBase třídy. Odvozování z  *\<typ >* animace nebo  *\<typ >* AnimationUsingKeyFrames třídy se nedoporučuje.  
  
### <a name="derive-from-typeanimationbase"></a>Jsou odvozeny z \<typ > AnimationBase  
 Odvozování z  *\<typ >* AnimationBase třída je nejjednodušší způsob, jak vytvořit nový typ animace. Tuto metodu použijte, pokud chcete vytvořit nový animace pro typ, který již má odpovídající  *\<typ >* AnimationBase třídy.  
  
 **Pokyny k implementaci**  
  
 Odvozovat  *\<typ >* animace třídy a implementovat metodu GetCurrentValueCore. Metoda GetCurrentValueCore vrátí aktuální hodnotu animace. Přijímá tři parametry: navrhované výchozí hodnoty, navrhované konečnou hodnotu a <xref:System.Windows.Media.Animation.AnimationClock>, kterou používáte k určení rozsahu postupu animace.  
  
 Protože  *\<typ >* AnimationBase třídy dědí z <xref:System.Windows.Freezable> třídy, je nutné také přepsat <xref:System.Windows.Freezable.CreateInstanceCore%2A> core vrací novou instanci třídy. Pokud třída nepoužívá vlastnosti závislosti k ukládání svých dat nebo vyžaduje dodatečnou inicializaci. po jeho vytvoření, možná budete muset přepsat další metody; Zobrazit [přehled Zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) Další informace.  
  
 Další informace najdete v dokumentaci k GetCurrentValueCore metodu pro  *\<typ >* AnimationBase třídy pro typ, který má být animován. Příklad najdete v tématu [ukázkové vlastní animace](https://go.microsoft.com/fwlink/?LinkID=159981)  
  
 **Alternativní přístupy**  
  
 Pokud chcete jednoduše změnit, jak jsou interpolovány hodnot animace, vzhledem k tomu odvození některého ze  *\<typ >* třídy klíčový snímek. Klíčový snímek, který vytvoříte, je možné s odpovídající  *\<typ >* AnimationUsingKeyFrames poskytované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="derive-from-animationtimeline"></a>Odvozovat třídu AnimationTimeline  
 Odvozovat <xref:System.Windows.Media.Animation.AnimationTimeline> třídy, pokud chcete vytvořit animaci pro typ, který ještě nemá odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace, nebo pokud chcete vytvořit animaci, která není silného typu.  
  
 **Pokyny k implementaci**  
  
 Odvozovat <xref:System.Windows.Media.Animation.AnimationTimeline> třídy a přepsat následující členy:  
  
-   <xref:System.Windows.Freezable.CreateInstanceCore%2A> – Pokud je konkrétní novou třídu, je nutné přepsat <xref:System.Windows.Freezable.CreateInstanceCore%2A> vrácení nové instance třídy.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> – Přepište tuto metodu za účelem vrácení aktuální hodnoty animace. Přijímá tři parametry: původní výchozí hodnotu, výchozí cíl hodnotu a <xref:System.Windows.Media.Animation.AnimationClock>. Použití <xref:System.Windows.Media.Animation.AnimationClock> k získání aktuálního času a průběhu pro animaci. Můžete zvolit, jestli se má použít výchozí hodnoty zdroj a cíl.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> – Tato vlastnost označující, zda animace používá výchozí cíl hodnotu zadanou pomocí přepsání <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> metody.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> – Přepsat tuto vlastnost umožňující označit, <xref:System.Type> výstupu animace vytvoří.  
  
 Pokud třída nepoužívá vlastnosti závislosti k ukládání svých dat nebo vyžaduje dodatečnou inicializaci. po jeho vytvoření, možná budete muset přepsat další metody; Zobrazit [přehled Zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) Další informace.  
  
 Doporučené paradigma (používané [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animací), je použít dvě úrovně dědičnosti:  
  
1.  Vytvořit abstraktní  *\<typ >* AnimationBase třída odvozená z <xref:System.Windows.Media.Animation.AnimationTimeline>. Tato třída by měly přepsat <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> metody. Měl by také zavést nové abstraktní metoda GetCurrentValueCore a přepsat <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> tak, aby ho ověří typy výchozí cílové hodnoty parametrů a výchozí hodnota, pak zavolá GetCurrentValueCore.  
  
2.  Vytvořit jiné třídy, která dědí z nové  *\<typ >* AnimationBase třídy a přepíše <xref:System.Windows.Freezable.CreateInstanceCore%2A> metody, metoda GetCurrentValueCore, která je zavedená, a <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> vlastnost.  
  
 **Alternativní přístupy**  
  
 Pokud chcete typ, který nemá žádné odpovídající animace od/Komu/kým a animace klíčových snímků animace, zvažte použití <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Protože je slabě typované, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> libovolný typ hodnoty lze animovat. Nevýhod tohoto přístupu je, že <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> podporuje pouze diskrétní interpolace.  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>Použití zpětného volání na rámec  
 Tuto metodu použijte, když budete chtít úplně obejít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace systému. Jeden scénář pro tento přístup je fyzika animace, kde na každou animaci kroku na nový směr nebo pozice animované objekty musí být přepočítány na základě poslední sadu interakce s objekty.  
  
 **Pokyny k implementaci**  
  
 Na rozdíl od dalších přístupů popsaných v tomto přehledu k použití na rámce zpětného volání není nutné k vytvoření třídy klíčových snímků nebo vlastní animace.  
  
 Místo toho si zaregistrujete <xref:System.Windows.Media.CompositionTarget.Rendering> události objektu, který obsahuje objekty, které má být animován. Tato metoda obslužné rutiny události volána jednou pro každý snímek. Pokaždé, když, který [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshals se nazývá trvalý vykreslování data ve vizuálním stromu ve stromové struktuře kompozice metodu obslužné rutiny události.  
  
 V obslužné rutině událostí, provádět vaše cokoli, co projeví výpočty, které jsou nezbytné pro animace a nastavte vlastnosti objektů má být animován s těmito hodnotami.  
  
 Získat čas prezentace aktuálního snímku <xref:System.EventArgs> přidružený k tomuto událostí můžete přetypovat jako <xref:System.Windows.Media.RenderingEventArgs>, které poskytují <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> vlastnost, která vám umožní získat aktuální rámec v vykreslování čas.  
  
 Další informace najdete v tématu <xref:System.Windows.Media.CompositionTarget.Rendering> stránky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.IKeyFrame>  
 [Přehled způsobů animace vlastností](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Přehled zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Přehled animací cesty](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled animace a systému časování](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Ukázka vlastních animací](https://go.microsoft.com/fwlink/?LinkID=159981)
