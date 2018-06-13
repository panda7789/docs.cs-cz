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
ms.openlocfilehash: 3f212cd89fe9fe1bcf95a374fa0cd92aedadefa9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558028"
---
# <a name="custom-animations-overview"></a>Přehled vlastních animací
Toto téma popisuje, jak a kdy rozšířit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace systému tak, že vytvoříte vlastní klíčových snímků animace třídy, nebo pomocí zpětného volání za rámce obejít ho.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Zjistit, v tomto tématu, měli byste se seznámit s různými typy animací poskytované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Další informace naleznete v přehledu animací From/To/By [klíč rámce animací přehled](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)a [cesta animací přehled](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md).  
  
 Vzhledem k tomu, že animace třídy dědí <xref:System.Windows.Freezable> třída, měli byste se seznámit s <xref:System.Windows.Freezable> objekty a postupy, jak dědit z <xref:System.Windows.Freezable>. Další informace najdete v tématu [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>Rozšíření systému animace  
 Existuje několik způsobů, jak rozšířit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému animace, v závislosti na úrovni integrovanou funkci, kterou chcete použít.  Existují tři body primární rozšíření v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace modul:  
  
-   Vytvoření objektu vlastní klíče rámce dědění z jednoho z  *\<typ >*@keyframe, které určuje třídy, jako například <xref:System.Windows.Media.Animation.DoubleKeyFrame>. Tento postup používá většina integrované funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modul animace.  
  
-   Vytvořit vlastní třídu animace dědění ze <xref:System.Windows.Media.Animation.AnimationTimeline> nebo jeden z  *\<typ >* třídy AnimationBase.  
  
-   Pomocí zpětného volání za rámce vygenerujte animací na základě za rámce. Tento přístup zcela obchází animace a časování systému.  
  
 Následující tabulka popisuje některé scénáře pro rozšíření systému animace.  
  
|Pokud chcete...|Tuto metodu použijte|  
|-------------------------|-----------------------|  
|Přizpůsobení interpolace mezi hodnotami typu, který má odpovídající  *\<typ >* AnimationUsingKeyFrames|Vytvořte vlastní klíče rámeček. Další informace najdete v tématu [vytvořte vlastní klíč rámeček](#createacustomkeyframe) části.|  
|Přizpůsobení více než jen interpolace mezi hodnotami typu, který má odpovídající  *\<typ >* animace.|Vytvořte vlastní animace třídu, která dědí z  *\<typ >* AnimationBase třídu, která odpovídá typu chcete animace. Další informace najdete v tématu [vytvoření vlastní třídy animace](#createacustomanimationtype) části.|  
|Animace typ, který nemá odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace|Použijte <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> nebo vytvořte třídu, která dědí z <xref:System.Windows.Media.Animation.AnimationTimeline>. Další informace najdete v tématu [vytvoření vlastní třídy animace](#createacustomanimationtype) části.|  
|Postupné animaci více objektů s hodnotami, které se vypočítávají každý rámečkem a jsou založené na poslední sadu objekt interakce|Použití zpětného volání za rámce. Další informace najdete v tématu [vytvořte zpětné volání za rámce použití](#useperframecallback) části.|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>Vytvořte vlastní klíče rámeček  
 Vytvoření třídy vlastní klíčových snímků je nejjednodušší způsob, jak rozšířit systém animace. Tuto metodu použijte, pokud chcete metodu různých interpolace pro klíč rámce animace.  Jak je popsáno v [klíč rámce animací přehled](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md), klíč rámce animace pomocí klíčových snímků objektů ke generování hodnot její výstup. Každý objekt klíčových snímků provádí tři funkce:  
  
-   Určuje cílový hodnoty pomocí jeho <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> vlastnost.  
  
-   Určuje dobu, kdy by mělo být dosaženo tuto hodnotu pomocí své <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> vlastnost.  
  
-   Argument interpolaci mezi hodnotou předchozí klíčových snímků a vlastní hodnotu implementací InterpolateValueCore metody.  
  
 **Pokyny pro implementaci**  
  
 Odvozena od  *\<typ >*@keyframe, které určuje abstraktní třídy a implementovat metodu InterpolateValueCore. Metoda InterpolateValueCore vrací aktuální hodnotu klíčového snímku. Jak dlouho trvá dva parametry: hodnota předchozí klíčových snímků a průběh hodnotu rozsahu od 0 do 1. Průběh 0 označuje klíče rámečku byl spuštěn, a hodnota 1 označuje, že klíče rámečku má právě dokončili a by měla vrátit hodnotu zadanou pomocí jeho <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> vlastnost.  
  
 Protože  *\<typ >*@keyframe, které určuje třídy dědí <xref:System.Windows.Freezable> třídy, je nutné také přepsat <xref:System.Windows.Freezable.CreateInstanceCore%2A> základní vrátit novou instanci třídy vašich. Pokud třída nepoužívá vlastností závislostí k ukládání dat nebo vyžaduje další inicializace po vytvoření, možná budete muset přepsat další metody; najdete v článku [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) Další informace.  
  
 Po vytvoření vaše vlastní  *\<typ >* animace klíčových snímků, můžete ji použít s  *\<typ >* AnimationUsingKeyFrames tohoto typu.  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>Vytvořte třídu vlastní animace  
 Vytváření vlastní animace typ nabízí větší kontrolu nad jak animovaný objekt v. Existují dva doporučené způsoby, jak vytvořit vlastní typ animace: odvozujete od <xref:System.Windows.Media.Animation.AnimationTimeline> třídy nebo  *\<typ >* třída AnimationBase. Odvozování z  *\<typ >* animace nebo  *\<typ >* AnimationUsingKeyFrames třídy se nedoporučuje.  
  
### <a name="derive-from-typeanimationbase"></a>Odvozena od \<typ > AnimationBase  
 Odvozování z  *\<typ >* AnimationBase třída je nejjednodušší způsob, jak vytvořit nový typ animace. Tuto metodu použijte, pokud chcete vytvořit nový animace pro typ, který již má odpovídající  *\<typ >* třída AnimationBase.  
  
 **Pokyny pro implementaci**  
  
 Odvozena od  *\<typ >* animace třídy a implementujte metodu GetCurrentValueCore. Metoda GetCurrentValueCore vrátí aktuální animace. Jak dlouho trvá tři parametry: hodnotou navrhované, navrhované koncovou hodnotu a <xref:System.Windows.Media.Animation.AnimationClock>, který použijete k určení průběh animace.  
  
 Protože  *\<typ >* AnimationBase třídy dědí <xref:System.Windows.Freezable> třídy, je nutné také přepsat <xref:System.Windows.Freezable.CreateInstanceCore%2A> základní vrátit novou instanci třídy třídě. Pokud třída nepoužívá vlastností závislostí k ukládání dat nebo vyžaduje další inicializace po vytvoření, možná budete muset přepsat další metody; najdete v článku [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) Další informace.  
  
 Další informace najdete v dokumentaci k GetCurrentValueCore metoda pro  *\<typ >* AnimationBase třídu pro typ, který chcete animace. Příklad, naleznete v části [vlastní animace ukázka](http://go.microsoft.com/fwlink/?LinkID=159981)  
  
 **Alternativní přístupy**  
  
 Pokud chcete jednoduše změnit, jak jsou hodnoty animace interpolované, vzhledem k tomu odvození některého ze  *\<typ >*@keyframe, které určuje třídy. Klíče rámečku vytvoříte lze použít s odpovídající  *\<typ >* AnimationUsingKeyFrames poskytované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="derive-from-animationtimeline"></a>Odvozena od AnimationTimeline  
 Odvozena od <xref:System.Windows.Media.Animation.AnimationTimeline> třídy, pokud chcete vytvořit animace pro typ, který ještě nemá odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace, nebo chcete vytvořit animace, která není silného typu.  
  
 **Pokyny pro implementaci**  
  
 Odvozena od <xref:System.Windows.Media.Animation.AnimationTimeline> třídy a přepsat následující členy:  
  
-   <xref:System.Windows.Freezable.CreateInstanceCore%2A> – Pokud je konkrétní novou třídu, je nutné přepsat <xref:System.Windows.Freezable.CreateInstanceCore%2A> vrátit novou instanci třídy třídě.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> – Přepište tuto metodu a vrátí aktuální hodnotu animace. Jak dlouho trvá tři parametry: výchozí hodnotu původu, výchozí hodnotu cílové a <xref:System.Windows.Media.Animation.AnimationClock>. Použití <xref:System.Windows.Media.Animation.AnimationClock> získat aktuální čas nebo průběhu pro animaci. Můžete zvolit, jestli se má použít výchozí původní a cílové hodnoty.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> – Přepsat tuto vlastnost k označení, zda vaše animace používá výchozí cílové hodnoty určené <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> metoda.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> – Tuto vlastnost k označení přepsat <xref:System.Type> výstupu vytváří animace.  
  
 Pokud třída nepoužívá vlastností závislostí k ukládání dat nebo vyžaduje další inicializace po vytvoření, možná budete muset přepsat další metody; najdete v článku [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) Další informace.  
  
 Doporučené zlepší (používané [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animací), je použít dvě úrovně dědičnosti:  
  
1.  Vytvoření abstraktní  *\<typ >* AnimationBase třída odvozená z <xref:System.Windows.Media.Animation.AnimationTimeline>. Tato třída by měly přepsat <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> metoda. Měl by také zavádět nové abstraktní metodu GetCurrentValueCore a přepsat <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> tak, aby ověřuje typy výchozí cílové hodnoty parametrů a výchozí hodnota počátku, pak zavolá GetCurrentValueCore.  
  
2.  Vytvořte jinou třídu, která dědí z nové  *\<typ >* AnimationBase třídy a přepíše <xref:System.Windows.Freezable.CreateInstanceCore%2A> metoda, GetCurrentValueCore metodu, která jste seznámili, a <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> vlastnost.  
  
 **Alternativní přístupy**  
  
 Pokud chcete animace typ, který nemá žádné odpovídající animace z/do nebo podle nebo animace jednotlivých klíč, zvažte použití <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Protože je slabě typované, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> můžete animace jakýkoli typ hodnoty. Z nevýhod tohoto přístupu je, že <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> podporuje pouze diskrétní interpolace.  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>Použití zpětného volání za rámce  
 Tuto metodu použijte, když potřebujete zcela vynechat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému animace. Jedním scénářem, tento přístup není fyziky animací, kde v každé animace krok nové směr nebo pozice animovaný objektů musí být přepočítávány na základě poslední sadu objekt interakce.  
  
 **Pokyny pro implementaci**  
  
 Na rozdíl od jiných přístupy popsané v tomto přehledu používat zpětného volání za rámce, nemusíte vytvoření třídy klíčových snímků nebo vlastní animace.  
  
 Místo toho můžete zaregistrovat <xref:System.Windows.Media.CompositionTarget.Rendering> události objektu, který obsahuje objekty, které chcete animace. Tato metoda obslužné rutiny události získá volá se jednou za snímek. Každý čas, který [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshals trvalou vykreslování data ve vizuálním stromu napříč stromu složení metodu obslužné rutiny událostí je volána.  
  
 V vaší obslužné rutiny událostí provádět vaší ať výpočty potřebné pro vaše animace ovlivňuje a nastavte vlastnosti objektů, které chcete animace s těmito hodnotami.  
  
 Získat prezentace době platný snímek, <xref:System.EventArgs> přidružen k této události lze převést jako <xref:System.Windows.Media.RenderingEventArgs>, která poskytnout <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> vlastnost, která vám pomůže získat aktuální snímek je vykreslování čas.  
  
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
 [Ukázka vlastní animace](http://go.microsoft.com/fwlink/?LinkID=159981)
