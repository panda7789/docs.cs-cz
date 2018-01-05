---
title: "Metadata vlastností závislosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b5c4ee554e8a0148c7d8d8044735f66778e7117
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="dependency-property-metadata"></a>Metadata vlastností závislosti
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Vlastnost metadata, systém, která přesahuje, může být hlášené o vlastnosti prostřednictvím reflexe nebo obecné generování sestav zahrnuje [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] charakteristiky. Metadata pro vlastnost závislosti lze také přiřadit jednoznačně podle třídy, která definuje vlastnost závislosti, jde změnit, pokud vlastnost závislosti je přidat do jiné třídy a je možné přepsat konkrétně všechny odvozené třídy, které dědí Vlastnost závislosti z definující základní třídy.  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastností závislostí z perspektivy příjemce existující vlastností závislostí na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídy a mít ke čtení [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Chcete-li v následujících příkladech v tomto tématu byste měli také porozumět [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a vědět, jak napsat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
<a name="dp_metadata_contents"></a>   
## <a name="how-dependency-property-metadata-is-used"></a>Používání metadat vlastností závislostí  
 Metadata vlastnosti závislost existuje jako objekt, který můžete zadat dotaz na charakteristiky vlastnosti závislosti. Tato metadata také přistupuje často vlastnosti systému jako zpracovává všechny danou vlastnost závislosti. Objekt metadat pro vlastnost závislosti může obsahovat následující typy informací:  
  
-   Výchozí hodnota pro vlastnost závislosti, pokud jiná hodnota lze stanovit pro vlastnost závislosti místní hodnota, styl, dědičnosti atd. Vyčerpávající diskusi o tom, jak výchozí hodnoty účastnit prioritu používá systém vlastnost při přiřazování hodnoty vlastností závislostí, najdete v části [přednost hodnota vlastnosti závislosti](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
-   Odkazy na implementace zpětného volání, které ovlivňují převod nebo upozornění na změnu chování na základě typu na vlastníka. Všimněte si, že tyto zpětná volání jsou často definovány s úrovní přístupu neveřejní tak získání skutečné odkazy z metadat není obecně možné pouze v případě odkazy jsou v rámci vašeho oboru povolený přístup. Další informace o vlastnosti závislosti zpětná volání, najdete v části [závislostí vlastnost zpětná volání a ověření](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
-   Pokud vlastnost závislosti dotyčném se považuje za vlastnost úrovni rozhraní WPF, metadata může obsahovat WPF úrovni rozhraní závislostí vlastnost vlastnostmi, které sestavy informace a stav služby, například úrovni rozhraní WPF rozložení modul a vlastnost dědičnosti logiku. Další informace o tento aspekt metadat vlastností závislostí v tématu [metadat vlastností Framework](../../../../docs/framework/wpf/advanced/framework-property-metadata.md).  
  
<a name="APIs"></a>   
## <a name="metadata-apis"></a>Metadat rozhraní API  
 Typ, který hlásí většinu informace o metadatech, které používá systém vlastnost je <xref:System.Windows.PropertyMetadata> třídy. Metadata instance jsou zadány volitelně při vlastností závislostí jsou registrované vlastnosti systému a lze jej zadat znovu pro další typy, které se přidaly jako vlastníci nebo přepsat metadat, který dědí ze základní třídy závislosti definici vlastnosti. (Pro případy, kdy registrace vlastnost neurčuje metadata, výchozí <xref:System.Windows.PropertyMetadata> je vytvořena s výchozími hodnotami pro tuto třídu.) Registrované metadata se vrátí jako <xref:System.Windows.PropertyMetadata> při volání různých <xref:System.Windows.DependencyProperty.GetMetadata%2A> přetížení, které získat metadata z vlastnost závislosti na <xref:System.Windows.DependencyObject> instance.  
  
 <xref:System.Windows.PropertyMetadata> Je pak třída odvozená z zajistit více konkrétních metadat pro architektury oddělení, jako jsou třídy úrovni rozhraní WPF. <xref:System.Windows.UIPropertyMetadata>Přidá animace reporting, a <xref:System.Windows.FrameworkPropertyMetadata> poskytuje vlastnosti úrovni rozhraní WPF uvedených v předchozí části. Když jsou vlastnosti závislosti registrováno, lze registrovat pomocí těchto <xref:System.Windows.PropertyMetadata> odvozených třídách. Když je zkontrolován metadata, základní <xref:System.Windows.PropertyMetadata> typ může potenciálně přetypovat odvozené třídy tak, aby můžete prozkoumat podrobnější vlastnosti.  
  
> [!NOTE]
>  Vlastnost charakteristiky, které lze zadat v <xref:System.Windows.FrameworkPropertyMetadata> jsou někdy označovány v této dokumentaci jako "příznaky". Při vytváření nové instance metadata pro použití v závislostí vlastnost registrace nebo přepsání metadata, zadáte tyto hodnoty pomocí flagwise výčtu <xref:System.Windows.FrameworkPropertyMetadataOptions> a potom zadejte pravděpodobně zřetězených hodnoty výčtu k <xref:System.Windows.FrameworkPropertyMetadata> konstruktor. Nicméně, po sestavený, tyto charakteristiky možnost jsou zveřejněné v rámci <xref:System.Windows.FrameworkPropertyMetadata> jako řadu logická hodnota vlastnosti, nikoli vytváření hodnota výčtu. Logická hodnota vlastnosti umožňují kontrolovat každý podmíněného, nikoli by bylo potřeba použít masky pro hodnotu výčtu flagwise získání informací o vás zajímá. Konstruktor používá zřetězených <xref:System.Windows.FrameworkPropertyMetadataOptions> abychom zachovali délka podpis konstruktor přiměřené, zatímco skutečná sestavené metadata zpřístupní diskrétní vlastnosti aby dotazování intuitivnější metadat.  
  
<a name="override_or_subclass"></a>   
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>Při přepsání Metadata, kdy na odvození třídy  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vlastnost systému bylo navázáno možnosti pro změnu vlastností závislostí některé vlastnosti bez nutnosti jejich být zcela znovu implementovaná. To se provádí uložených na konkrétní typ vytváření jinou instanci metadat vlastností pro vlastnost závislosti. Všimněte si, že většina existující vlastnosti závislosti nejsou vlastnosti virtuálního tak přesněji řečeno "znovu"jejich implementaci na zděděné třídy jenom je možné dosáhnout pomocí stínový provoz existujícího člena.  
  
 Pokud tento scénář se pokoušíte povolit pro vlastnost závislosti na typu nelze dosáhnout úpravou vlastností existující vlastností závislostí, se může pak bude nutné vytvořit odvozené třídy a pak deklarovat vlastnost vlastní závislosti v odvozené třídě. Vlastnost vlastní závislosti se chová stejně vlastností závislostí, které jsou definované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]. Další podrobnosti o vlastnostech vlastní závislosti najdete v tématu [vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
 Jeden významné znakem vlastnost závislosti, které nelze přepsat je její typ hodnoty. Pokud jsou dědí vlastnosti závislost, která má přibližnou chování budete potřebovat, ale vyžadují různé typ pro něj, je nutné implementovat vlastnost vlastní závislosti a případně propojit vlastnosti prostřednictvím převod typu nebo jiné implementace na vaše vlastní třídy. Navíc nelze nahradit existující <xref:System.Windows.ValidateValueCallback>, protože tento zpětného volání existuje v samotné pole registrace a není v rámci jeho metadata.  
  
<a name="scenarios"></a>   
## <a name="scenarios-for-changing-existing-metadata"></a>Scénáře pro změnu existující Metadata  
 Při práci s metadaty existující vlastnost závislosti, chcete-li změnit výchozí hodnota je jeden běžný scénář pro změnu metadat vlastností závislostí. Změna nebo přidání zpětná volání vlastnost systému je pokročilejší scénáře. Můžete to udělat, pokud vaši implementaci do odvozené třídy má jiný vzájemné vztahy mezi vlastností závislostí. Jedním z podmíněné příkazy toho, že programovací model, který podporuje kód a deklarativní využití je, že musíte povolit vlastnosti se nastavuje v libovolném pořadí. Proto všechny závislé vlastnosti je nutné nastavit v běhu bez kontextu a nelze spoléhat na vědomí, že nastavení pořadí může najít, jako v konstruktoru. Další informace o tento aspekt vlastnosti systému, naleznete v části [závislostí vlastnost zpětná volání a ověření](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md). Všimněte si, že zpětná volání ověření nejsou součástí metadat; jsou součástí identifikátoru vlastnosti závislosti. Zpětná volání ověření proto nelze změnit přepsáním metadata.  
  
 V některých případech můžete také chtít změnit možnosti metadata vlastnosti úrovni rozhraní WPF na existující vlastností závislostí. Tyto možnosti komunikovat určitých známých podmíněné příkazy o vlastnostech úrovni rozhraní WPF jiným procesům úrovni rozhraní WPF například systém rozložení.  Nastavení možnosti obecně provádí jenom v případě, že registrace novou vlastnost závislosti, ale je také možné změnit metadata vlastnosti úrovni rozhraní WPF v rámci <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> nebo <xref:System.Windows.DependencyProperty.AddOwner%2A> volání. Konkrétní hodnoty, které mají být použity a další informace naleznete v části [metadat vlastností Framework](../../../../docs/framework/wpf/advanced/framework-property-metadata.md). Další informace týkající se jak tyto možnosti by měla být nastavena pro vlastnost nově zaregistrovaný závislosti najdete v tématu [vlastní závislosti vlastnosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
<a name="dp_override_metadata"></a>   
### <a name="overriding-metadata"></a>Přepsání metadat  
 Účelem přepsání metadat je primárně, takže máte možnost, chcete-li změnit různé chování odvozené metadata, která se použijí pro vlastnost závislosti, protože existuje u vašeho typu. Důvody této jsou vysvětleny v další části [Metadata](#dp_metadata_contents) části. Další informace včetně některé příklady kódu najdete v tématu [přepsat Metadata pro vlastnost závislosti](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).  
  
 Metadata vlastnosti můžete zadat pro vlastnost závislosti během volání registrace (<xref:System.Windows.DependencyProperty.Register%2A>). V mnoha případech můžete však zadat metadata specifická pro typ pro třídu tehdy, když ho dědí tuto vlastnost závislosti. To provedete pomocí volání <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metoda.  Příklad z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], <xref:System.Windows.FrameworkElement> třída je typ, který nejprve zaregistruje <xref:System.Windows.UIElement.Focusable%2A> vlastnost závislosti. Ale <xref:System.Windows.Controls.Control> třída přepíše metadata pro vlastnost závislosti definovat vlastní počáteční výchozí hodnotu, změna z `false` k `true`a v opačném případě znovu použije původní <xref:System.Windows.UIElement.Focusable%2A> implementace.  
  
 Při přepsání metadata vlastnosti rozdílná metadata jsou sloučit nebo nahradit.  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>sloučí. Pokud přidáte nový <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, že zpětné volání je uložená v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v hodnotě přepsání <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> se vyzval jako odkaz z nejbližším podřízeném objektu, který je zadaný v metadatech.  
  
-   Skutečné vlastnost chování systému pro <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> je, že jsou uchovány a přidat do tabulky, s pořadí provádění systémem vlastnost tom, že se zpětná volání nejvíce odvozené třídy jsou vyvolány nejprve implementace všech vlastníků metadata v hierarchii.  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A>nahrazuje. Pokud nezadáte <xref:System.Windows.PropertyMetadata.DefaultValue%2A> v hodnotě přepsání <xref:System.Windows.PropertyMetadata.DefaultValue%2A> pochází z nejbližším podřízeném objektu, který je zadaný v metadatech.  
  
-   <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>implementace jsou nahrazena. Pokud přidáte nový <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, že zpětné volání je uložená v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v hodnotě přepsání <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> se vyzval jako odkaz z nejbližším podřízeném objektu, který je zadaný v metadatech.  
  
-   Vlastnost chování systému je pouze <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> ve okamžitou metadata volat. Žádné odkazy na jiné <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementace v hierarchii se zachovají.  
  
 Toto chování je implementováno modulem <xref:System.Windows.PropertyMetadata.Merge%2A>a je možné přepsat na metadata odvozené třídy.  
  
#### <a name="overriding-attached-property-metadata"></a>Přepsání Metadata přidružená vlastnost  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], připojené vlastnosti jsou implementované jako vlastnosti závislosti. To znamená, že mají také metadata vlastnosti, které jednotlivé třídy můžete přepsat. Oboru aspekty přidružená vlastnost v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou obecně který <xref:System.Windows.DependencyObject> může mít připojená vlastnost nastavená na nich. Proto všechny <xref:System.Windows.DependencyObject> může přepsat metadata přidružená vlastnost, protože je nastaven na instanci třídy. Můžete přepsat výchozí hodnoty, zpětná volání nebo vlastnosti reporting vlastnosti úrovni rozhraní WPF. Pokud je připojená vlastnost nastavená na instanci třídě, ty přepsat metadat vlastností, které vlastnosti použít. Například můžete přepsat výchozí hodnotu tak, aby hodnota přepsání je ohlášeny jako hodnotu připojená vlastnost instancí třídy, vždy, když není vlastnost jinak nastavena.  
  
> [!NOTE]
>  <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> Vlastnost není relevantní pro přidružené vlastnosti.  
  
<a name="dp_add_owner"></a>   
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>Přidání třídy jako vlastníka existující vlastnost závislosti  
 Třídu můžete přidat sám sebe jako vlastníka vlastnosti závislost, která je již zaregistrován, pomocí <xref:System.Windows.DependencyProperty.AddOwner%2A> metoda. To umožňuje používat vlastnost závislosti, který byl původně zaregistrován pro jiný typ třídy. Přidání třídy není obvykle odvozené třídy typu, který nejprve zaregistrovat tuto vlastnost závislosti jako vlastníka. Efektivně to umožňuje třídě a odvozených tříd pro "dědění" implementace vlastností závislostí bez třídě původního vlastníka a přidání třída je ve stejné hierarchii true třídy. Také přidání – třída (a také všechny odvozené třídy) jim pak můžou metadata specifická pro typ pro původní vlastnost závislosti.  
  
 A také přidání sám sebe jako vlastník prostřednictvím metody nástroje Vlastnosti systému, by měly přidání třídy sám na sobě deklarovat další veřejné členy, aby bylo možné vlastnost závislosti] úplné účastnit systém vlastnost s vystavení kódu a kódu . Třída, která přidává existující vlastnost závislosti má stejné odpovědnosti, pokud je to stejně třídu, která definuje novou vlastnost vlastní závislosti vystavení objektový model pro tuto vlastnost závislosti. První je tento člen vystavit pole identifikátoru vlastnosti závislosti. Toto pole musí mít `public static readonly` pole typu <xref:System.Windows.DependencyProperty>, který je přiřazen k vrácenou hodnotu <xref:System.Windows.DependencyProperty.AddOwner%2A> volání. Je druhý člen k definování [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost "obálku". Obálku umožňuje pohodlnější k manipulaci s vaší vlastnost závislosti v kódu (zabránit volání <xref:System.Windows.DependencyObject.SetValue%2A> každý čas a volání této pouze jednou v samotné obálku). Obálku je implementováno stejně jako na tom, jak se by implementovat Pokud byly registrace vlastnost vlastní závislosti. Další informace o implementaci vlastnost závislosti najdete v tématu [vlastní závislosti vlastnosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) a [přidat typ vlastníka pro vlastnost závislosti](../../../../docs/framework/wpf/advanced/how-to-add-an-owner-type-for-a-dependency-property.md).  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner a přidružené vlastnosti  
 Můžete volat <xref:System.Windows.DependencyProperty.AddOwner%2A> pro vlastnost závislosti, který je definován jako přidružená vlastnost v třídě vlastníka. Obecně je důvodem pro tento vystavit dříve přidružená vlastnost jako vlastnost závislosti není připojena. Pak bude vystavovat <xref:System.Windows.DependencyProperty.AddOwner%2A> vrátí hodnotu jako `public static readonly` pole pro použití jako vlastnost identifikátor závislosti a definují vlastnosti příslušné "obálky" tak, aby vlastnost se zobrazí v tabulce členy a podporuje vlastnost nepřipojené použití v třídě.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.PropertyMetadata>  
 <xref:System.Windows.DependencyObject>  
 <xref:System.Windows.DependencyProperty>  
 <xref:System.Windows.DependencyProperty.GetMetadata%2A>  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Metadata vlastnosti architektury](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)
