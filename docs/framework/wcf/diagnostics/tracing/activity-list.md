---
title: Seznam aktivit
ms.date: 03/30/2017
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
ms.openlocfilehash: f96aab037e86b05096df7ffc82a0be3f6cce1ad2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998033"
---
# <a name="activity-list"></a>Seznam aktivit
Toto téma obsahuje seznam všech aktivit, které jsou definované ve Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  Můžete také definovat aktivity prostřednictvím kódu programu do skupiny uživatelů trasování. Další informace najdete v tématu [generování trasování v uživatelském kódu](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
## <a name="servicemodel-activities"></a>Aktivity ServiceModel  
 Následující tabulka uvádí všechny aktivity pro použití hlavní scénáře.  
  
|Popisek|Název aktivity|Typ aktivity|Popis|  
|-----------|-------------------|-------------------|-----------------|  
|A, M|Ambientní aktivity|Není k dispozici (to není řízen ServiceModel)|Aktivita, jejíž ID je nastavena v TLS před všechna volání do modelu kódu (na straně klienta nebo na straně serveru).<br /><br /> Příklad: Kde je volán otevřít na klienta WCF nebo serviceHost.open aktivita je volána.|  
|B|Konstrukce<br /><br /> Třídu ChannelFactory. ContractType: '[Type]'.|Konstrukce||  
|C|Otevřít<br /><br /> [ClientBase&#124;ChannelFactory]. ContractType: '[Type]'.|Otevřít||  
|I|Zavřít [třídu ClientBase&#124;ChannelFactory]. ContractType: '[Type]'.|Zavřít||  
|M|Vytvořte třídu ServiceHost. ServiceType: '[Type]'.|Konstrukce||  
|N|Otevřete třídu ServiceHost. ServiceType: '[Type]'.|Otevřít||  
|Z|Ukončete třídu ServiceHost. ServiceType: '[Type]'.|Zavřít||  
|O|Naslouchá na [address].|ListenAt|Tato a další aktivity jsou specifické pro přenos. Aktivita ListenAt reprezentuje obsah, který se mapuje na adresu, ve kterém naslouchá naslouchací proces kanálu v. V případě služby MSMQ je samotný fronty od fronty se mapuje na jednu adresu. Tato aktivita poslouchá příchozí připojení v případě připojení objektově orientovaný přenosy pro zprávy služby MSMQ v případě služby MSMQ. Tato aktivita se vytvoří během ServiceHost.Open() a obsahuje trasování týkající se vytváření a odstraňování naslouchací proces, jakož i přenosu navýšení kapacity pro všechny aktivity ReceiveBytes.|  
|P|Přijměte bajty v připojení [address]. Zobrazí se zpráva služby MSMQ.|ReceiveBytes|V rámci této aktivity je zpracovat data, která se nakonec zpráva WCF. Příchozí bajty jsou čekalo se v případě připojením řízenou přepravou nebo http. Pro protokol TCP nebo pojmenovaného kanálu životního cyklu této aktivity je životnost připojení, jakmile je vytvořena při vytvoření připojení. Pro protokol http je doba života zprávy požadavku a vzniká, pokud je zpráva odeslána. Tato aktivita obsahuje trasování týkající se vytváření a rušení připojení, pokud je k dispozici, jakož i přenosy navýšení kapacity pro všechny aktivity zpracování zprávy (objekt).<br /><br /> V případě služby MSMQ je aktivita kde načtení zprávy služby MSMQ.|  
|Q|Zpracovat zprávu [číslo]. (Poznámka: [číslo] se zvětšující hodnotu, která se spouští v 1.)|ProcessMessage|Zpracování příchozí zprávy. Tato aktivita spustí, když jsou přijata veškerá data (bajty, zprávy služby MSMQ) a vytvoří objekt zprávy WCF. Trasování v rámci této aktivity se zabývají zpracování záhlaví.<br /><br /> Jakmile je vytvořen zprávu, která se dají odeslat, aktivita ServiceHost ProcessAction přepnutí na po vyhledání odpovídající ID aktivity|  
|D, S|Zpracujte akci [action].|ProcessAction|Příjem zprávy přes zásobník Transport/Security/RM pro odeslání zprávy do uživatelského kódu v procesu a v opačném pořadí při odeslání.<br /><br /> Na serveru tato aktivita používá rozšíří ID aktivity, pokud je odeslána do záhlaví zprávy přes "Šíření aktivity"; v opačném případě se vytvoří nový identifikátor GUID.<br /><br /> V této aktivitě také zpracování zprávy s odpovědí pro kontrakty požadavku/odpovědi.|  
|T|Spusťte [IContract.Operation].|ExecuteUserCode|Spuštění uživatelského kódu po odeslání na straně služby. Tato aktivita poskytuje hranice od sebe odděluje kód ServiceHost z uživatelského kódu.|  
  
## <a name="security-activities"></a>Aktivity související se zabezpečením  
 V následující tabulce jsou uvedeny všechny aktivity související se zabezpečením.  
  
|Název aktivity|Typ aktivity|Popis|  
|-------------------|-------------------|-----------------|  
|Nastavte zabezpečenou relaci|SetupSecurity|Existuje na straně klienta. Obsahuje všechny RVNÍ * / SCT vymění pro ověřování a nastavení kontextu zabezpečení. Pokud `propagateActivity` = `true`, tato aktivita je sloučen s služby odpovídající proces akce RVNÍ\*/SCT aktivity.|  
|Zavřít zabezpečenou relaci|SetupSecurity|Existuje na straně klienta. Obsahuje výměně zpráv Storno pro ukončení relace zabezpečení. Pokud `propagateActivity` = `true`, tato aktivita je sloučen s akce proces "Storno" ze služby.|  
  
 V následující tabulce jsou uvedeny všechny aktivity související s modelu COM +.  
  
|Název aktivity|Typ aktivity|Popis|  
|-------------------|-------------------|-----------------|  
|Vytvoří instanci modelu COM +|TransferToCOMPlus|pro každý modelu COM + 1 instance aktivity volat z kódu WCF|  
|Spuštění modelu COM + \<operace >|TransferToCOMPlus|pro každý modelu COM + 1 instance aktivity volat z kódu WCF|  
  
## <a name="wmi-activities"></a>Aktivity služby WMI  
 V následující tabulce jsou uvedeny všechny aktivity související s WMI.  
  
|Název aktivity|Typ aktivity|Popis|  
|-------------------|-------------------|-----------------|  
|Získání rozhraní WMI|WMIGetObject|Uživatel načítá data z rozhraní WMI.|  
|Put rozhraní WMI|WmiPutInstance|Uživatel je aktualizace dat pomocí rozhraní WMI.|
