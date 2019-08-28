---
title: Vlastní kritérium hledání
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 236cce194d89409ab19732c239459418cddd251b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039944"
---
# <a name="custom-find-criteria"></a>Vlastní kritérium hledání
Tato ukázka předvádí, jak vytvořit vlastní rozsah odpovídající pomocí logiky a jak implementovat vlastní službu zjišťování. Klienti používají funkce pro přizpůsobení vlastního oboru k upřesnění a dalšímu sestavování nad funkcemi vyhledávání WCF poskytované systémem. Scénář tohoto příkladu se zabývá následujícím způsobem:  
  
1. Klient hledá službu kalkulačky.  
  
2. Aby bylo možné upřesnit jeho hledání, musí klient používat vlastní pravidlo pro porovnání s oborem.  
  
3. Podle tohoto pravidla služba odpoví zpátky na klienta, pokud jeho koncový bod odpovídá jakémukoli rozsahu určenému klientem.  
  
## <a name="demonstrates"></a>Demonstruje  
  
- Vytvoření vlastní služby zjišťování.  
  
- Implementace vlastního oboru se shoduje s algoritmem.  
  
## <a name="discussion"></a>Účely  
 Klient hledá kritéria pro porovnání typu nebo. Služba odpoví zpátky, pokud obory ve svých koncových bodech odpovídají jakémukoli rozsahu, který poskytuje klient. V takovém případě klient hledá službu kalkulačky, která má některý z oborů v následujícím seznamu:  
  
1. `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2. `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3. `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 K tomu klient směruje služby tak, aby používaly vlastní obor porovnávání pravidla, a to předáním vlastního oboru odpovídajícímu identifikátoru URI. Aby bylo možné zajistit vlastní rozsah porovnávání, musí služba používat vlastní službu zjišťování, která rozumí vlastnímu pravidlu pro shodu oboru a implementuje přidruženou odpovídající logiku.  
  
 V projektu klienta otevřete soubor Program.cs. Všimněte si, `ScopeMatchBy` že pole `FindCriteria` objektu je nastaveno na konkrétní identifikátor URI. Tento identifikátor je odeslán do služby. Pokud služba toto pravidlo nezná, ignoruje žádost klienta o vyhledání.  
  
 Otevřete projekt služby. K implementaci služby pro vlastní zjišťování se používají tři soubory:  
  
1. **AsyncResult.cs**: Toto je implementace rozhraní `AsyncResult` , které je vyžadováno metodami zjišťování.  
  
2. **CustomDiscoveryService.cs**: Tento soubor implementuje službu pro vlastní zjišťování. Implementace rozšiřuje <xref:System.ServiceModel.Discovery.DiscoveryService> třídu a přepíše nezbytné metody. Poznamenejte si implementaci <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> metody. Metoda zkontroluje, zda je v klientovi zadána shoda vlastního oboru podle pravidla. Jedná se o stejný vlastní identifikátor URI, který dříve zadal klient. Je-li zadáno vlastní pravidlo, je uvedena cesta kódu, která implementuje logiku "nebo" shody.  
  
     Tato vlastní logika projde všechny obory na každém z koncových bodů, které má služba. Pokud některý z rozsahů koncového bodu odpovídá jakémukoli oboru poskytovanému klientem, služba zjišťování přidá tento koncový bod do odpovědi, která se pošle zpátky klientovi.  
  
3. **CustomDiscoveryExtension.cs**: Posledním krokem při implementaci služby zjišťování je připojení této implementace vlastní zjišťovací služby k hostiteli služby. Pomocná třída použitá zde je `CustomDiscoveryExtension` třída. Tato třída rozšiřuje <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> třídu. Uživatel musí přepsat <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> metodu. V tomto případě metoda vrátí instanci vlastní služby zjišťování, která byla vytvořena před. `PublishedEndpoints`je a <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> , který obsahuje všechny koncové body aplikace, které jsou přidány <xref:System.ServiceModel.ServiceHost>do. Služba vlastní zjišťování tuto službu používá k naplnění svého interního seznamu. Uživatel může také přidat další metadata koncového bodu.  
  
 Nakonec otevřete Program.cs. Všimněte si, že <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a `CustomDiscoveryExtension` jsou přidány do hostitele. Jakmile se tato možnost provede a hostitel má koncový bod pro příjem zpráv zjišťování, může aplikace použít službu Custom Discovery.  
  
 Pozor, aby klient mohl najít službu bez znalosti její adresy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Otevřete řešení, které obsahuje projekt.  
  
2. Sestavte projekt.  
  
3. Spusťte aplikaci služby.  
  
4. Spusťte klientskou aplikaci.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
