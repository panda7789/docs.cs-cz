---
title: Vlastní kritérium hledání
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 699260fcef7680710f721d213dbf1126ebf7a896
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400774"
---
# <a name="custom-find-criteria"></a>Vlastní kritérium hledání
Tato ukázka předvádí, jak vytvořit vlastní obor shoda pomocí logiky a jak implementovat vlastní zjišťování služby. Klienti používají vlastní obor funkci přiřazování k upřesnění a další postaveny funkce poskytované systémem hledání zjišťování WCF. Scénář, který obsahuje tato ukázka je následujícím způsobem:  
  
1.  Klient hledá službu kalkulačky.  
  
2.  Upřesněte své hledání, klient musí použít vlastní obor pravidlo pro porovnávání.  
  
3.  Podle tohoto pravidla odpoví služby zpět do klienta, pokud svůj koncový bod odpovídá některému z oborů určená klientem.  
  
## <a name="demonstrates"></a>Demonstruje  
  
-   Vytvoření vlastní zjišťování služby.  
  
-   Implementace vlastní obor shoda algoritmem.  
  
## <a name="discussion"></a>Diskuse  
 Klient hledá "Nebo" typ odpovídající kritériím. Služba zpět odpovídá, pokud obory na své koncové body shodují s některým z obory poskytnuté klientem. V tomto případě klient hledá službu kalkulačky, která obsahuje některý z obory v následujícím seznamu:  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 K tomu, přesměruje klienta služby použít vlastní pravidlo pro porovnávání předáním ve vlastní obor identifikátorem URI oboru. Usnadnit odpovídající vlastní obor služby musíte použít vlastní zjišťování služby rozumí pravidla shody vlastní obor, který implementuje přidružené odpovídající logiky.  
  
 V klientském projektu otevřete soubor Program.cs. Všimněte si, že `ScopeMatchBy` pole `FindCriteria` je nastaven na konkrétní identifikátor URI. Tento identifikátor je odeslána do služby. Pokud služba nerozumí toto pravidlo, ignoruje požadavek klienta najít.  
  
 Otevřete projekt služby. Pro implementaci této vlastní zjišťování služby se používají tři soubory:  
  
1.  **AsyncResult.cs**: Toto je implementace `AsyncResult` , který vyžaduje metody zjišťování.  
  
2.  **CustomDiscoveryService.cs**: Tento soubor implementuje vlastní zjišťování služby. Rozšiřuje implementaci <xref:System.ServiceModel.Discovery.DiscoveryService> třídy a přepíše nezbytné metody. Všimněte si, provádění <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> metody. Metoda zkontroluje, zda byl zadán vlastní obor shoda pravidlem klientem. Toto je stejný vlastní identifikátor URI, který klient zadali dřív. Pokud je zadán vlastní pravidlo, je a potom do cesty kódu, který implementuje shoda logiky "Nebo".  
  
     Tato vlastní logiku prochází všechny obory ve všech koncových bodů, které má služba. Pokud některý z koncového bodu obory shodují s některým z obory poskytnuté klientem, přidá službu zjišťování tohoto koncového bodu do odpovědi, která je odeslána zpět klientovi.  
  
3.  **CustomDiscoveryExtension.cs**: poslední krok při provádění zjišťování služby je pro tuto implementaci vlastní připojení zjišťování služby na hostitele služby. Je pomocnou třídu použitou tady `CustomDiscoveryExtension` třídy. Tato třída rozšiřuje <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> třídy. Uživatel musí přepsat <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> metody. V tomto případě vrátí metoda instance služby vlastní zjišťování, který byl vytvořen ještě před. `PublishedEndpoints` je <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> , která obsahuje všechny koncové body aplikace, které jsou přidány do <xref:System.ServiceModel.ServiceHost>. Vlastní zjišťování služby to používá k naplnění jeho vnitřní seznam. Uživatel může pro přidání dalších koncový bod metadat.  
  
 A konečně otevřete soubor Program.cs. Všimněte si, jak <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a `CustomDiscoveryExtension` jsou přidány do hostitele. Jakmile se to a že hostitel má koncový bod, přes které se budou přijímat zprávy zjišťování může aplikace použít vlastní zjišťování služby.  
  
 Podívejte se, že je klient nemůže najít službu bez znalosti jeho adresu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Otevřete řešení, které obsahuje projekt.  
  
2.  Sestavte projekt.  
  
3.  Spuštění služby aplikace.  
  
4.  Spuštění klientské aplikace.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
