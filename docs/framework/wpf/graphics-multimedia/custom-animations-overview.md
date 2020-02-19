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
ms.openlocfilehash: 5a9ca51b87f73a24b90d0bd843ee306f8a1b970a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453088"
---
# <a name="custom-animations-overview"></a>Přehled vlastních animací
Toto téma popisuje, jak a kdy se má zvětšit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animační systém vytvořením vlastních klíčových snímků, tříd animace nebo pomocí zpětného volání pro obejít ho v rámci snímku.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Předpoklady  
 Pro pochopení tohoto tématu byste měli být obeznámeni s různými typy animací poskytovaných [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Další informace najdete v tématu Přehled animací od/k/podle, přehled [animací klíčových snímků](key-frame-animations-overview.md)a [Přehled animací cest](path-animations-overview.md).  
  
 Vzhledem k tomu, že třídy animace dědí z <xref:System.Windows.Freezable> třídy, měli byste být obeznámeni s objekty <xref:System.Windows.Freezable> a o tom, jak dědit z <xref:System.Windows.Freezable>. Další informace najdete v tématu [Přehled objektů Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>Rozšíření animačního systému  
 Existuje několik způsobů, jak použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animační systém v závislosti na úrovni integrovaných funkcí, které chcete použít.  V modulu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace existují tři primární body rozšiřitelnosti:  
  
- Vytvořte vlastní objekt rámce klíče děděním z jednoho z *\<typu >* třídy klíčového snímku, jako je <xref:System.Windows.Media.Animation.DoubleKeyFrame>. Tento přístup využívá většinu integrovaných funkcí modulu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animace.  
  
- Vytvořte vlastní třídu animace děděním z <xref:System.Windows.Media.Animation.AnimationTimeline> nebo jednoho z *\<typu >* třídy AnimationBase.  
  
- Použití zpětného volání pro jednotlivé snímky ke generování animací na základě jednotlivých snímků. Tento přístup zcela obchází systém animace a časování.  
  
 Následující tabulka popisuje některé scénáře pro rozšíření animačního systému.  
  
|Když chcete...|Použít tento přístup|  
|-------------------------|-----------------------|  
|Přizpůsobení interpolace mezi hodnotami typu, který má odpovídající *typ\<>* AnimationUsingKeyFrames|Vytvořte vlastní klíčový snímek. Další informace najdete v části [Vytvoření vlastního klíčového snímku](#createacustomkeyframe) .|  
|Přizpůsobte více než pouze interpolaci mezi hodnotami typu, který má odpovídající *typ\<>* animaci.|Vytvořte vlastní třídu animace, která dědí z *typu\<>* třídy AnimationBase, která odpovídá typu, který chcete animovat. Další informace naleznete v části [Vytvoření vlastní třídy animace](#createacustomanimationtype) .|  
|Animace typu, který nemá žádnou odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animaci|Použijte <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> nebo vytvořte třídu, která dědí z <xref:System.Windows.Media.Animation.AnimationTimeline>. Další informace naleznete v části [Vytvoření vlastní třídy animace](#createacustomanimationtype) .|  
|Animace více objektů s hodnotami, které jsou vypočítány každý rámec a jsou založeny na poslední sadě interakcí objektů|Použití zpětného volání pro jednotlivé snímky. Další informace najdete v části [vytvoření zpětného volání pro použití v rámci jednotlivých snímků](#useperframecallback) .|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>Vytvořit vlastní klíčový snímek  
 Vytvoření vlastního klíčového rámce je nejjednodušší způsob, jak se systém animace rozšiřuje. Tento postup použijte, pokud chcete pro animaci klíčových snímků použít jinou metodu interpolace.  Jak je popsáno v tématu [Přehled animací](key-frame-animations-overview.md)klíčových snímků, animace klíčových snímků používá objekty klíčových snímků ke generování výstupních hodnot. Každý objekt rámce klíče provádí tři funkce:  
  
- Určuje cílovou hodnotu pomocí vlastnosti <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>.  
  
- Určuje čas, kdy se má tato hodnota dosáhnout pomocí vlastnosti <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>.  
  
- Interpoluje hodnotu předchozího klíčového snímku a jeho vlastní hodnotu implementací metody InterpolateValueCore.  
  
 **Pokyny k implementaci**  
  
 Odvození z *\<typu >* abstraktní třídy klíčového snímku a implementace metody InterpolateValueCore Metoda InterpolateValueCore vrací aktuální hodnotu klíčového snímku. Používá dva parametry: hodnotu předchozího klíčového snímku a hodnotu průběhu, která je v rozsahu od 0 do 1. Průběh 0 značí, že se klíčový snímek právě zahájil, a hodnota 1 označuje, že se klíčový snímek právě dokončil a že by měl vracet hodnotu určenou vlastností <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>.  
  
 Vzhledem k tomu, že *typ\<>* třídy klíčového snímku dědí z třídy <xref:System.Windows.Freezable>, je také nutné přepsat <xref:System.Windows.Freezable.CreateInstanceCore%2A> Core a vrátit novou instanci vaší třídy. Pokud Třída nepoužívá vlastnosti závislosti k ukládání dat nebo vyžaduje po vytvoření dodatečnou inicializaci, může být nutné přepsat další metody; Další informace najdete v tématu [Přehled objektů Freezable](../advanced/freezable-objects-overview.md) .  
  
 Po vytvoření vlastního *typu\<>* animaci klíčového snímku ho můžete použít s *typem\<>* pro tento typ AnimationUsingKeyFrames.  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>Vytvoření vlastní třídy animace  
 Vytvořením vlastního typu animace získáte větší kontrolu nad tím, jak objekt je animovaný. Existují dva doporučené způsoby vytvoření vlastního typu animace: můžete odvozovat z třídy <xref:System.Windows.Media.Animation.AnimationTimeline> nebo *\<typu >* třídy AnimationBase. Odvození z *typu\<>* animace nebo *typu\<>* třídy AnimationUsingKeyFrames se nedoporučuje.  
  
### <a name="derive-from-typeanimationbase"></a>Odvození z \<typu > AnimationBase  
 Odvozením *typu\<>* třídy AnimationBase je nejjednodušší způsob, jak vytvořit nový typ animace. Tento postup použijte, pokud chcete vytvořit novou animaci pro typ, který již má odpovídající *\<typ >* třídy AnimationBase.  
  
 **Pokyny k implementaci**  
  
 Je odvozen z *\<typu >* třídy animace a implementuje metodu GetCurrentValueCore. Metoda GetCurrentValueCore vrátí aktuální hodnotu animace. Používá tři parametry: navrhovaná počáteční hodnota, navrhovaná koncová hodnota a <xref:System.Windows.Media.Animation.AnimationClock>, které slouží k určení průběhu animace.  
  
 Vzhledem k tomu, že *\<typ >* třídy AnimationBase dědí z třídy <xref:System.Windows.Freezable>, je také nutné přepsat <xref:System.Windows.Freezable.CreateInstanceCore%2A> Core a vrátit novou instanci vaší třídy. Pokud Třída nepoužívá vlastnosti závislosti k ukládání dat nebo vyžaduje po vytvoření dodatečnou inicializaci, může být nutné přepsat další metody; Další informace najdete v tématu [Přehled objektů Freezable](../advanced/freezable-objects-overview.md) .  
  
 Další informace naleznete v dokumentaci metody GetCurrentValueCore pro typ *\<>* třídy AnimationBase pro typ, který chcete animovat. Příklad najdete v [ukázce vlastního animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation) .  
  
 **Alternativní přístupy**  
  
 Pokud jednoduše chcete změnit způsob, jakým jsou Interpolované hodnoty animace, s ohledem na odvození z jednoho z *\<typu >* třídy klíčového snímku. Klíčový snímek, který vytvoříte, lze použít s odpovídajícím *typem\<>* AnimationUsingKeyFrames poskytované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="derive-from-animationtimeline"></a>Odvodit z třídu AnimationTimeline  
 Je odvozena od třídy <xref:System.Windows.Media.Animation.AnimationTimeline>, pokud chcete vytvořit animaci pro typ, který ještě nemá odpovídající animaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], nebo chcete vytvořit animaci, která není silného typu.  
  
 **Pokyny k implementaci**  
  
 Odvodit z třídy <xref:System.Windows.Media.Animation.AnimationTimeline> a přepsat následující členy:  
  
- <xref:System.Windows.Freezable.CreateInstanceCore%2A> – Pokud je vaše nová třída konkrétní, je nutné přepsat <xref:System.Windows.Freezable.CreateInstanceCore%2A> a vrátit novou instanci vaší třídy.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> – tuto metodu přepište, pokud chcete vrátit aktuální hodnotu animace. Používá tři parametry: výchozí počáteční hodnotu, výchozí cílová hodnota a <xref:System.Windows.Media.Animation.AnimationClock>. K získání aktuálního času nebo průběhu animace použijte <xref:System.Windows.Media.Animation.AnimationClock>. Můžete zvolit, jestli se mají používat výchozí zdrojové a cílové hodnoty.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> – tuto vlastnost přepište, pokud chcete určit, jestli vaše animace používá výchozí cílovou hodnotu určenou metodou <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>.  
  
- <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> – tuto vlastnost můžete přepsat tak, aby označovala <xref:System.Type> výstupu, který vaše animace generuje.  
  
 Pokud Třída nepoužívá vlastnosti závislosti k ukládání dat nebo vyžaduje po vytvoření dodatečnou inicializaci, může být nutné přepsat další metody; Další informace najdete v tématu [Přehled objektů Freezable](../advanced/freezable-objects-overview.md) .  
  
 Doporučené paradigma (používané pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animací) je použití dvou úrovní dědičnosti:  
  
1. Vytvořte abstraktní *\<typ >* třídu AnimationBase, která je odvozena z <xref:System.Windows.Media.Animation.AnimationTimeline>. Tato třída by měla přepsat metodu <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>. Měla by také zavést novou abstraktní metodu, GetCurrentValueCore a přepsat <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> tak, aby ověřovala typy výchozí hodnoty původu a výchozích parametrů cílové hodnoty, a pak volá GetCurrentValueCore.  
  
2. Vytvořte další třídu, která dědí z vašeho nového *\<typu >* třídy AnimationBase a přepíše metodu <xref:System.Windows.Freezable.CreateInstanceCore%2A>, metodu GetCurrentValueCore, kterou jste zavedli, a vlastnost <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>.  
  
 **Alternativní přístupy**  
  
 Pokud chcete animovat typ, který nemá žádnou odpovídající z animace/na/podle animace nebo animace klíčových snímků, zvažte použití <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Vzhledem k tomu, že je typově slabá, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> může animovat jakýkoli typ hodnoty. Nevýhodou tohoto přístupu je, že <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> podporuje pouze samostatnou interpolaci.  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>Použití zpětného volání pro jednotlivé snímky  
 Tento postup použijte v případě, že potřebujete zcela obejít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animační systém. Jedním z scénářů tohoto přístupu jsou fyzika animace, kde v každém kroku animace je nutné přepočítat nový směr nebo polohu animovaných objektů na základě poslední sady interakcí objektů.  
  
 **Pokyny k implementaci**  
  
 Na rozdíl od jiných přístupů popsaných v tomto přehledu, pro použití zpětného volání pro jednotlivé snímky nemusíte vytvářet vlastní animaci nebo třídu klíčových snímků.  
  
 Místo toho se zaregistrujete na událost <xref:System.Windows.Media.CompositionTarget.Rendering> objektu, který obsahuje objekty, které chcete animovat. Tato metoda obslužné rutiny události se volá jednou pro každý snímek. Pokaždé, když [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zachová trvalá data vykreslování ve vizuálním stromu napříč stromu kompozice, je volána metoda obslužné rutiny události.  
  
 V obslužné rutině události proveďte libovolné výpočty potřebné pro efekt animace a nastavte vlastnosti objektů, které mají být s těmito hodnotami animovány.  
  
 Chcete-li získat čas prezentace aktuálního rámce, <xref:System.EventArgs> přidružené k této události lze přetypovat jako <xref:System.Windows.Media.RenderingEventArgs>, která poskytuje vlastnost <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A>, kterou lze použít k získání času vykreslování aktuálního rámce.  
  
 Další informace najdete na stránce <xref:System.Windows.Media.CompositionTarget.Rendering>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.IKeyFrame>
- [Přehled způsobů animace vlastností](property-animation-techniques-overview.md)
- [Přehled zablokovatelných objektů](../advanced/freezable-objects-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Přehled animací cesty](path-animations-overview.md)
- [Přehled animace](animation-overview.md)
- [Přehled animace a systému časování](animation-and-timing-system-overview.md)
- [Ukázka vlastní animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/CustomAnimation)
