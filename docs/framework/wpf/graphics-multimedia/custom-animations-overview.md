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
ms.openlocfilehash: c5f315992e8ae37bc79602e6986d90e7af591fb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186553"
---
# <a name="custom-animations-overview"></a>Přehled vlastních animací
Toto téma popisuje, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a kdy rozšířit systém animace vytvořením vlastní klíčové snímky, animace třídy nebo pomocí zpětného volání na snímek obejít.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Chcete-li porozumět tomuto tématu, měli byste se seznámit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]s různými typy animací poskytovaných rozhraním . Další informace naleznete v tématu Přehled animací od/do/podle, [přehled animací klíčových snímků](key-frame-animations-overview.md)a [přehled animací cesty](path-animations-overview.md).  
  
 Vzhledem k tomu, <xref:System.Windows.Freezable> že třídy animace <xref:System.Windows.Freezable> dědí z <xref:System.Windows.Freezable>třídy, měli byste být obeznámeni s objekty a jak dědit z . Další informace naleznete v přehledu [mrazivých objektů](../advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>
## <a name="extending-the-animation-system"></a>Rozšíření animačního systému  
 Existuje několik způsobů, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozšířit systém animace, v závislosti na úrovni vestavěné funkce, které chcete použít.  V modulu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace jsou tři primární body rozšiřitelnosti:  
  
- Vytvořte vlastní objekt klíčového snímku děděním z jedné <xref:System.Windows.Media.Animation.DoubleKeyFrame>z tříd * \<Type>* KeyFrame, například . Tento přístup používá většinu vestavěné funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modulu animace.  
  
- Vytvořte vlastní třídu animace <xref:System.Windows.Media.Animation.AnimationTimeline> děděním z nebo z jedné z * \<tříd Type>* AnimationBase.  
  
- Pomocí zpětného volání na snímek můžete generovat animace na základě počtu snímků. Tento přístup zcela obchází animaci a časování systému.  
  
 Následující tabulka popisuje některé scénáře pro rozšíření systému animace.  
  
|Když chceš...|Použít tento přístup|  
|-------------------------|-----------------------|  
|Přizpůsobení interpolace mezi hodnotami typu, * \< *který má odpovídající typ>AnimationUsingKeyFrames|Vytvořte vlastní klíčový snímek. Další informace naleznete v části [Vytvoření vlastního klíčového snímku.](#createacustomkeyframe)|  
|Přizpůsobte více než jen interpolaci mezi * \< *hodnotami typu, který má odpovídající typ>animace.|Vytvořte vlastní animační třídu, která dědí z třídy * \<Type>* AnimationBase, která odpovídá typu, který chcete animovat. Další informace naleznete v části [Vytvoření vlastní třídy animace.](#createacustomanimationtype)|  
|Animace typu, který nemá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] žádnou odpovídající animaci|Použijte <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> nebo vytvořte třídu, <xref:System.Windows.Media.Animation.AnimationTimeline>která dědí z . Další informace naleznete v části [Vytvoření vlastní třídy animace.](#createacustomanimationtype)|  
|Animace více objektů s hodnotami, které jsou vypočítány v každém rámci a jsou založeny na poslední sadě interakcí objektů|Použijte zpětné volání za snímek. Další informace naleznete v části [Vytvoření zpětného volání pomocí za rámci.](#useperframecallback)|  
  
<a name="createacustomkeyframe"></a>
## <a name="create-a-custom-key-frame"></a>Vytvoření vlastního klíčového snímku  
 Vytvoření vlastní třídy klíčových snímků je nejjednodušší způsob, jak rozšířit systém animace. Tento přístup použijte, pokud chcete použít jinou metodu interpolace pro animaci klíčových snímků.  Jak je popsáno v [přehledu animací klíčových snímků](key-frame-animations-overview.md), animace klíčových snímků používá objekty klíčových snímků ke generování výstupních hodnot. Každý objekt klíčového snímku provádí tři funkce:  
  
- Určuje cílovou hodnotu <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> pomocí své vlastnosti.  
  
- Určuje čas, kdy má být dosaženo <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> této hodnoty pomocí své vlastnosti.  
  
- Interpoluje mezi hodnotou předchozího klíčového snímku a jeho vlastní hodnotou implementací metody InterpolateValueCore.  
  
 **Pokyny k implementaci**  
  
 Odvodit z * \<type>* KeyFrame abstraktní třídy a implementovat InterpolateValueCore metoda. Metoda InterpolateValueCore vrátí aktuální hodnotu klíčového snímku. Trvá dva parametry: hodnota předchozí klíčový snímek a hodnota průběhu, která se pohybuje od 0 do 1. Průběh 0 označuje klíčový snímek právě začal a hodnota 1 označuje, že klíčový snímek právě <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> dokončena a by měla vrátit hodnotu určenou jeho vlastnost.  
  
 Vzhledem k tomu, * \<že třídy Type>* <xref:System.Windows.Freezable.CreateInstanceCore%2A> KeyFrame dědí z <xref:System.Windows.Freezable> třídy, musíte také přepsat jádro, abyste vrátili novou instanci vaší třídy. Pokud třída nepoužívá vlastnosti závislostí k ukládání dat nebo vyžaduje další inicializaci po vytvoření, může být nutné přepsat další metody; Další informace naleznete v [přehledu mrazivých objektů.](../advanced/freezable-objects-overview.md)  
  
 Po vytvoření vlastní * \< *animace Typ>klíčových rámců ji můžete použít s * \<typem>* AnimationUsingKeyFrames pro tento typ.  
  
<a name="createacustomanimationtype"></a>
## <a name="create-a-custom-animation-class"></a>Vytvoření vlastní třídy animací  
 Vytvoření vlastního typu animace poskytuje větší kontrolu nad tím, jak objekt v animovaném objektu. Existují dva doporučené způsoby, jak vytvořit vlastní typ <xref:System.Windows.Media.Animation.AnimationTimeline> animace: můžete odvodit z třídy nebo * \<Type>* AnimationBase třídy. Odvození z * \<tříd Type>* Animation nebo * \<Type>* AnimationUsingKeyFrames se nedoporučuje.  
  
### <a name="derive-from-typeanimationbase"></a>Odvodit z \<typu>AnimationBase  
 Odvození z * \<třídy Type>* AnimationBase je nejjednodušší způsob, jak vytvořit nový typ animace. Tento přístup použijte, pokud chcete vytvořit novou animaci * \< *pro typ, který již má odpovídající type>AnimationBase třídy.  
  
 **Pokyny k implementaci**  
  
 Odvodit z * \<Type>* Animation třídy a implementovat GetCurrentValueCore metoda. Metoda GetCurrentValueCore vrátí aktuální hodnotu animace. Trvá tři parametry: navrhovaná počáteční hodnota, doporučená koncová <xref:System.Windows.Media.Animation.AnimationClock>hodnota a , které slouží k určení průběhu animace.  
  
 Vzhledem k tomu, * \<že třídy Type>* <xref:System.Windows.Freezable.CreateInstanceCore%2A> AnimationBase dědí z <xref:System.Windows.Freezable> třídy, musíte také přepsat jádro, abyste vrátili novou instanci vaší třídy. Pokud třída nepoužívá vlastnosti závislostí k ukládání dat nebo vyžaduje další inicializaci po vytvoření, může být nutné přepsat další metody; Další informace naleznete v [přehledu mrazivých objektů.](../advanced/freezable-objects-overview.md)  
  
 Další informace naleznete v dokumentaci metody GetCurrentValueCore pro třídu * \<Type>* AnimationBase pro typ, který chcete animovat. Příklad například viz [Ukázka vlastní animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)  
  
 **Alternativní přístupy**  
  
 Pokud chcete jednoduše změnit způsob interpolace hodnot animace, zvažte odvození z jedné z tříd * \<Type>* KeyFrame. Klíčový snímek, který vytvoříte, lze použít s odpovídajícím [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] * \<typem>* AnimationUsingKeyFrames poskytované .  
  
### <a name="derive-from-animationtimeline"></a>Odvodit z AnimationTimeline  
 Odvodit z <xref:System.Windows.Media.Animation.AnimationTimeline> třídy, pokud chcete vytvořit animaci pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typ, který ještě nemá odpovídající animaci, nebo chcete vytvořit animaci, která není silně zadaný.  
  
 **Pokyny k implementaci**  
  
 Odvodit z třídy <xref:System.Windows.Media.Animation.AnimationTimeline> a přepsat následující členy:  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A>– Pokud je nová třída konkrétní, <xref:System.Windows.Freezable.CreateInstanceCore%2A> je nutné přepsat vrátit novou instanci vaší třídy.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>– Přepsat tuto metodu vrátit aktuální hodnotu animace. Trvá tři parametry: výchozí zdroj hodnotu, výchozí <xref:System.Windows.Media.Animation.AnimationClock>cílovou hodnotu a . Použijte <xref:System.Windows.Media.Animation.AnimationClock> k získání aktuálního času nebo průběhu animace. Můžete zvolit, zda chcete použít výchozí hodnoty původu a cíle.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>– Přepsat tuto vlastnost k označení, zda animace používá <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> výchozí cílovou hodnotu určenou metodou.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>– Přepsat tuto vlastnost <xref:System.Type> k označení výstupu animace vytváří.  
  
 Pokud třída nepoužívá vlastnosti závislostí k ukládání dat nebo vyžaduje další inicializaci po vytvoření, může být nutné přepsat další metody; Další informace naleznete v [přehledu mrazivých objektů.](../advanced/freezable-objects-overview.md)  
  
 Doporučené paradigma (používané [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace) je použít dvě úrovně dědičnosti:  
  
1. Vytvořte abstraktní * \<třídu Type>* <xref:System.Windows.Media.Animation.AnimationTimeline>AnimationBase, která je odvozena od aplikace . Tato třída by <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> měla přepsat metodu. Měl by také zavést novou abstraktní metodu GetCurrentValueCore a přepsat <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> tak, aby ověřoval typy výchozí hodnoty původu a výchozí parametry cílové hodnoty a pak volá GetCurrentValueCore.  
  
2. Vytvořte jinou třídu, * \< *která dědí z nové <xref:System.Windows.Freezable.CreateInstanceCore%2A> třídy Type>AnimationBase a přepíše <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> metodu, metodu GetCurrentValueCore, kterou jste zavedli, a vlastnost.  
  
 **Alternativní přístupy**  
  
 Pokud chcete animovat typ, který nemá žádné odpovídající from/to/by animace <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>nebo animace klíčových snímků, zvažte použití . Vzhledem k tomu, že <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> je slabě zadaný, může animovat libovolný typ hodnoty. Nevýhodou tohoto přístupu <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> je, že podporuje pouze diskrétní interpolaci.  
  
<a name="useperframecallback"></a>
## <a name="use-per-frame-callback"></a>Použití zpětného volání za rámci  
 Tento přístup použijte, pokud potřebujete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zcela obejít animační systém. Jedním z scénářů pro tento přístup je fyzika animace, kde v každém kroku animace nový směr nebo umístění animovaných objektů je třeba přepočítat na základě poslední sady interakcí objektů.  
  
 **Pokyny k implementaci**  
  
 Na rozdíl od jiných přístupů popsaných v tomto přehledu, chcete-li použít zpětná volání na snímek, není nutné vytvářet vlastní animaci nebo třídu klíčových snímků.  
  
 Místo toho se <xref:System.Windows.Media.CompositionTarget.Rendering> zaregistrujete pro událost objektu, který obsahuje objekty, které chcete animovat. Tato metoda obslužné rutiny události se nazývá jednou za snímek. Pokaždé, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] když zařazuje trvalá data vykreslování ve vizuálním stromu do stromu složení, je volána metoda obslužné rutiny události.  
  
 V obslužné rutině události proveďte všechny výpočty nezbytné pro animační efekt a nastavte vlastnosti objektů, které chcete animovat s těmito hodnotami.  
  
 Chcete-li získat čas prezentace aktuálního rámce, <xref:System.EventArgs> přidružené k <xref:System.Windows.Media.RenderingEventArgs>této události <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> lze přetypovat jako , které poskytují vlastnost, kterou můžete použít k získání aktuálního rámce vykreslování čas.  
  
 Další informace naleznete <xref:System.Windows.Media.CompositionTarget.Rendering> na stránce.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [Přehled způsobů animace vlastností](property-animation-techniques-overview.md)
- [Přehled zablokovatelných objektů](../advanced/freezable-objects-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Přehled animací cesty](path-animations-overview.md)
- [Přehled animace](animation-overview.md)
- [Animace a časování přehledu systému](animation-and-timing-system-overview.md)
- [Ukázka vlastní animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)
