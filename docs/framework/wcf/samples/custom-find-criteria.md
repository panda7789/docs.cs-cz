---
title: "Vlastní kritérium hledání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31b599bc1086fcbfe8db527155d078299309a647
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="custom-find-criteria"></a>Vlastní kritérium hledání
Tento příklad znázorňuje, jak vytvořit vlastní rozsah odpovídající pomocí logiky a jak implementovat vlastní zjišťování služby. Klienti používají k zpřesnění a další sestavení nad funkce poskytované systémem najít zjišťování WCF vlastní rozsah odpovídající funkce. Scénáře, který popisuje tato ukázka je následující:  
  
1.  Klient hledá službu kalkulačky.  
  
2.  Upřesněte hledání, klient musí použít obor vlastní pravidlo pro porovnávání.  
  
3.  Podle tohoto pravidla odpoví služby zpět do klienta, pokud svůj koncový bod odpovídá některému z rozsahy určené klientem.  
  
## <a name="demonstrates"></a>Demonstruje  
  
-   Vytvoření vlastní zjišťování služby.  
  
-   Implementace odpovídající vlastní rozsah algoritmem.  
  
## <a name="discussion"></a>Diskusní  
 Klient hledá "Nebo" typ odpovídající kritériím. Služby zpět odpoví, je-li obory na své koncové body odpovídat oborů zadaných klientem. V tomto případě klient hledá službu kalkulačky, která obsahuje některý z oborů v následujícím seznamu:  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 K tomu, přesměruje klienta pro použití obor vlastní pravidlo pro porovnávání předáním porovnání vlastní rozsah identifikátorem URI. Usnadňuje odpovídající vlastní rozsah služby musíte použít vlastní zjišťování služba, která jste srozuměni s tím pravidla shody vlastní rozsah a přidružené logiky odpovídající implementuje.  
  
 V projektu klienta otevřete soubor Program.cs. Všimněte si, že `ScopeMatchBy` pole z `FindCriteria` je nastavena na konkrétní identifikátor URI. Tento identifikátor se odešle do služby. Pokud službu nerozumí toto pravidlo, ignoruje požadavek klienta najít.  
  
 Otevřete projekt služby. Tři soubory se používají k implementaci vlastních zjišťování služby:  
  
1.  **AsyncResult.cs**: Toto je implementace `AsyncResult` který je vyžadován na základě metody zjišťování.  
  
2.  **CustomDiscoveryService.cs**: Tento soubor implementuje vlastní zjišťování služby. Implementace rozšiřuje <xref:System.ServiceModel.Discovery.DiscoveryService> třídy a přepíše nezbytné metody. Poznámka: implementace <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> metoda. Metoda zkontroluje, zda byl zadán vlastní rozsah shody pravidlem klientem. Toto je stejný vlastní identifikátor URI, který klient zadali dřív. Pokud je zadán vlastní pravidlo, je následovaný kódová cesta, který implementuje logiku shodu "Nebo".  
  
     Tato vlastní logiky projde všechny obory ve všech koncových bodů, které má služba. Pokud se žádné rozsahy pro koncový bod shodují oborů poskytnutý klientem, přidá službu zjišťování tohoto koncového bodu do odpovědi, která je odeslána zpět klientovi.  
  
3.  **CustomDiscoveryExtension.cs**: poslední krok při provádění zjišťování služby je připojení Tato implementace vlastní zjišťování služby na hostitele služby. Pomocná třída použít zde je `CustomDiscoveryExtension` třídy. Tato třída rozšiřuje <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> třídy. Uživatel musí přepsat <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> metoda. V takovém případě metoda vrací instanci třídy služby vlastní zjišťování, který byl vytvořen ještě před. `PublishedEndpoints`je <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> obsahující všechny koncové body aplikace, které jsou přidány do <xref:System.ServiceModel.ServiceHost>. Služba vlastní zjišťování to používá k naplnění svůj vnitřní seznam. Uživatel může přidat další koncový bod metadata.  
  
 Nakonec otevřete Program.cs. Všimněte si, že jak <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a `CustomDiscoveryExtension` jsou přidány do hostitele. Jakmile to provádí a hostitele má koncový bod pro které bude přijímat zprávy zjišťování, aplikace můžete použít vlastní zjišťování služby.  
  
 Zkontrolujte, že klient je možné najít službu, aniž by věděly, jeho adresy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete řešení obsahující projekt.  
  
2.  Sestavte projekt.  
  
3.  Spusťte aplikaci služby.  
  
4.  Spusťte klientskou aplikaci.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
