---
title: Seznam aktivit
ms.date: 03/30/2017
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
ms.openlocfilehash: dc504c37b21a2d457f270331ab917747bafbb022
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="activity-list"></a>Seznam aktivit
Toto téma uvádí všechny aktivity, které jsou definované ve Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  Můžete také definovat aktivity prostřednictvím kódu programu ke skupině uživatelů trasování. Další informace najdete v tématu [generování trasování v uživatelském kódu](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
## <a name="servicemodel-activities"></a>Aktivity ServiceModel  
 Následující tabulka uvádí všechny aktivity pro scénáře hlavní použití.  
  
|Popisek|Název aktivity|Typ aktivity|Popis|  
|-----------|-------------------|-------------------|-----------------|  
|A, M|Vedlejším aktivity|Není k dispozici (Toto není řídí ServiceModel)|Aktivita, jejíž ID je nastavena v TLS před volání ServiceModel kódu (na straně klienta nebo na straně serveru).<br /><br /> Příklad: Aktivita kde je volán otevřete na [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] klienta nebo serviceHost.open je volána.|  
|B|Konstrukce<br /><br /> ChannelFactory. ContractType: '[Type]'.|Konstrukce||  
|C|Otevřít<br /><br /> [Třídu ClientBase&#124;ChannelFactory]. ContractType: '[Type]'.|Otevřít||  
|I|Zavřít [třídu ClientBase&#124;ChannelFactory]. ContractType: '[Type]'.|Zavřít||  
|M|Vytvořte třídu ServiceHost. ServiceType: '[Type]'.|Konstrukce||  
|N|Otevřete ServiceHost. ServiceType: '[Type]'.|Otevřít||  
|Z|Zavřete ServiceHost. ServiceType: '[Type]'.|Zavřít||  
|O|Naslouchat na [address].|ListenAt|Tato a další aktivity jsou specifické pro přenos. Aktivita ListenAt reprezentuje obsah, který se mapuje na adresu, na kterém naslouchá naslouchací proces kanálu nástroje v. V případě služby MSMQ je fronty samotné vzhledem k tomu, že mapuje fronty na jednu adresu. Tato aktivita poslouchá příchozí připojení v případě přenosů orientovaná na připojení, pro zprávy služby MSMQ v případě služby MSMQ. Tato aktivita se vytvoří během ServiceHost.Open() a obsahuje trasování týkající se vytvoření a uvolnění naslouchací proces, jakož i přenosu se pro všechny aktivity ReceiveBytes.|  
|P|Přijatých bajtů na připojení [address]. Zobrazí zpráva služby MSMQ.|ReceiveBytes|V této aktivitě, data, která bude nakonec získat [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zpráva se zpracuje. Příchozí bajty jsou čekali v případě orientovaná na připojení přenosu nebo http. Pro TCP nebo pojmenovaného kanálu životnost tuto aktivitu je životnost připojení, jako je vytvořen při vytváření připojení. Pro protokol http je životnosti žádost o zprávu a se vytvoří, když je zpráva odeslána. Tato aktivita obsahuje trasování týkající se vytvoření a uvolnění připojení, pokud je k dispozici, jakož i přenosy se pro všechny aktivity zpracování zprávy (objekt).<br /><br /> V případě služby MSMQ je aktivita kde načtení zprávy služby MSMQ.|  
|Q|Proces zpráva [číslo]. (Poznámka: [číslo] je rovnoměrně se zvětšující hodnotu, která začíná na 1.)|ProcessMessage|Proces příchozí zprávy. Tato aktivita se spustí po doručení všech dat (bajtů, zprávy služby MSMQ) do formuláře [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] objekt zprávy. Trasování v rámci této aktivity řešit zpracování záhlaví.<br /><br /> Jakmile je vytvořen zprávu, která může být odeslána, ServiceHost ProcessAction aktivity je přepnutá na po vyhledávání odpovídající ID aktivity|  
|D, S|Zpracování akce [akce].|ProcessAction|Proces, zobrazí se zpráva přes protokolů přenosu, zabezpečení nebo RM pro odeslání zprávy do uživatelského kódu na, a v obráceném pořadí na odeslání.<br /><br /> Na serveru tato aktivita používá šířený ID aktivity, pokud se odešlou v záhlaví zprávy prostřednictvím "Rozšíření aktivity"; jinak se vytvoří nový identifikátor GUID.<br /><br /> Zpráva odpovědi pro požadavek nebo odpověď kontrakty se také zpracovává aktivity.|  
|T|Spusťte [IContract.Operation].|ExecuteUserCode|Spuštění uživatelského kódu po odeslání na straně služby. Tato aktivita poskytuje hranici od sebe odděluje ServiceHost kód z kódu zadaný uživatelem.|  
  
## <a name="security-activities"></a>Aktivity související se zabezpečením  
 V následující tabulce jsou uvedeny všechny aktivity související se zabezpečením.  
  
|Název aktivity|Typ aktivity|Popis|  
|-------------------|-------------------|-----------------|  
|Instalační program zabezpečené relace|SetupSecurity|Existuje na straně klienta. Obsahuje všechny RVNÍ * / SCT výměny pro ověřování a nastavení kontext zabezpečení. Pokud `propagateActivity` = `true`, tato aktivita je sloučen s služby odpovídající procesu akce RVNÍ\*/SCT aktivity.|  
|Zavřít zabezpečené relace|SetupSecurity|Existuje na straně klienta. Obsahuje výměnu zpráv Storno pro ukončení zabezpečené relace. Pokud `propagateActivity` = `true`, tato aktivita je sloučen s akce proces "Zrušit" ze služby.|  
  
 V následující tabulce jsou uvedeny všechny činnosti týkající se modelu COM +.  
  
|Název aktivity|Typ aktivity|Popis|  
|-------------------|-------------------|-----------------|  
|Vytvoření instance modelu COM +|TransferToCOMPlus|instance 1 aktivity pro každé volání modelu COM + z [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] kódu|  
|Spuštění modelu COM + \<operaci >|TransferToCOMPlus|instance 1 aktivity pro každé volání modelu COM + z [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] kódu|  
  
## <a name="wmi-activities"></a>Aktivity služby WMI  
 V následující tabulce jsou uvedeny všechny aktivity související s WMI.  
  
|Název aktivity|Typ aktivity|Popis|  
|-------------------|-------------------|-----------------|  
|Get rozhraní WMI|WMIGetObject|Uživatel načítá data z rozhraní WMI.|  
|Put rozhraní WMI|WmiPutInstance|Uživatel je aktualizace dat pomocí rozhraní WMI.|
