---
title: Vlastní kritérium hledání
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 3bafe89f5c114106eece02c41599cf485591c1cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183864"
---
# <a name="custom-find-criteria"></a>Vlastní kritérium hledání
Tato ukázka ukazuje, jak vytvořit vlastní shodu oboru pomocí logiky a jak implementovat vlastní službu zjišťování. Klienti používají vlastní funkce porovnávání oboru k upřesnění a dalšímu sestavení nad funkcí vyhledávání WCF Discovery poskytovanou systémem. Scénář, který pokrývá tato ukázka, je následující:  
  
1. Klient hledá službu kalkulačky.  
  
2. Chcete-li upřesnit jeho hledání, klient musí použít vlastní pravidlo pro přizpůsobení oboru.  
  
3. Podle tohoto pravidla služba odpoví zpět klientovi, pokud jeho koncový bod odpovídá některému z oborů určených klientem.  
  
## <a name="demonstrates"></a>Demonstruje  
  
- Vytvoření vlastní služby zjišťování.  
  
- Implementace vlastní obor shoda podle algoritmu.  
  
## <a name="discussion"></a>Diskuse  
 Klient hledá kritéria pro shodovat s typem "OR". Služba odpoví zpět, pokud obory na jeho koncových bodů odpovídají některé z oborů poskytovaných klientem. V tomto případě klient hledá službu kalkulačky, která má některý z oborů v následujícím seznamu:  
  
1. `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2. `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3. `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Chcete-li to provést, klient nasměruje služby použít vlastní pravidlo pro porovnávání oboru předáním v vlastní obor shody uri. Chcete-li usnadnit vlastní obor odpovídající, služba musí používat vlastní zjišťování služby, která chápe vlastní obor odpovídající pravidlo a implementuje přidružené odpovídající logiku.  
  
 V klientském projektu otevřete soubor Program.cs. Všimněte `ScopeMatchBy` si, `FindCriteria` že pole objektu je nastaveno na konkrétní identifikátor URI. Tento identifikátor je odeslán službě. Pokud služba nerozumí tomuto pravidlu, ignoruje požadavek klienta na hledání.  
  
 Otevřete projekt služby. K implementaci služby Custom Discovery Service se používají tři soubory:  
  
1. **AsyncResult.cs**: Toto je `AsyncResult` implementace, která je vyžadována discovery metody.  
  
2. **CustomDiscoveryService.cs**: Tento soubor implementuje vlastní službu zjišťování. Implementace rozšiřuje třídu <xref:System.ServiceModel.Discovery.DiscoveryService> a přepíše nezbytné metody. Všimněte si <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> implementace metody. Metoda zkontroluje, zda byl vlastní obor odpovídající pravidlu určen klientem. Jedná se o stejný vlastní identifikátor URI, který klient zadal dříve. Pokud je zadáno vlastní pravidlo, je dodržena cesta kódu, která implementuje logiku shody "OR".  
  
     Tato vlastní logika prochází všechny obory na každém koncovém bodu, který má služba. Pokud některý z oborů koncového bodu odpovídají některému z oborů poskytovaných klientem, služba zjišťování přidá tento koncový bod k odpovědi, která je odeslána zpět klientovi.  
  
3. **CustomDiscoveryExtension.cs**: Posledním krokem při implementaci služby zjišťování je připojení této implementace vlastní zjišťovací služby k hostiteli služby. Pomocná třída, která `CustomDiscoveryExtension` se zde používá, je třída. Tato třída rozšiřuje <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> třídu. Uživatel musí přepsat <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> metodu. V tomto případě metoda vrátí instanci vlastní zjišťování služby, která byla vytvořena před. `PublishedEndpoints`<xref:System.Collections.ObjectModel.ReadOnlyCollection%601> je, který obsahuje všechny koncové body aplikace, <xref:System.ServiceModel.ServiceHost>které jsou přidány do . Vlastní služba zjišťování používá k naplnění svého vnitřního seznamu. Uživatel může přidat další metadata koncového bodu také.  
  
 Nakonec otevřete Program.cs. Všimněte si, že oba <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a `CustomDiscoveryExtension` jsou přidány do hostitele. Jakmile je to hotovo a hostitel má koncový bod, přes který chcete přijímat zprávy zjišťování, aplikace můžete použít vlastní zjišťování služby.  
  
 Všimněte si, že klient je schopen najít službu bez znalosti její adresy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Otevřete řešení, které obsahuje projekt.  
  
2. Sestavte projekt.  
  
3. Spusťte aplikaci služby.  
  
4. Spusťte klientskou aplikaci.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
