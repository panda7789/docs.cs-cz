---
title: Seznam aktivit
ms.date: 03/30/2017
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
ms.openlocfilehash: 8d43cc878d54efbd4908f92c3405bef2c7956f94
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602164"
---
# <a name="activity-list"></a>Seznam aktivit
V tomto tématu jsou uvedeny všechny aktivity definované pomocí Windows Communication Foundation (WCF).  
  
> [!NOTE]
> Aktivity můžete také definovat programově k seskupení trasování uživatele. Další informace najdete v tématu [generování trasování uživatelského kódu](emitting-user-code-traces.md).  
  
## <a name="servicemodel-activities"></a>Aktivity ServiceModel  
 V následující tabulce jsou uvedeny všechny aktivity pro hlavní scénáře použití.  
  
|Popisek|Název aktivity|Typ aktivity|Popis|  
|-----------|-------------------|-------------------|-----------------|  
|A, M|Okolní aktivita|Není k dispozici (Tato služba není řízena ServiceModel)|Aktivita, jejíž ID je nastaveno v TLS před všemi voláními do kódu ServiceModel (strana na straně klienta nebo serveru).<br /><br /> Příklad: aktivita, kde je volána metoda Open, je volána u klienta služby WCF nebo serviceHost. Open.|  
|B|Konstrukce<br /><br /> Tříd. ContractType: ' [typ] '.|Konstrukce||  
|C|Otevřít<br /><br /> [ClientBase&#124;třída ChannelFactory]. ContractType: ' [typ] '.|Otevřít||  
|I|Zavřete [ClientBase&#124;ChannelFactory]. ContractType: ' [typ] '.|Zavřít||  
|M|Sestavte třídu ServiceHost. ServiceType: ' [typ] '.|Konstrukce||  
|N|Otevřete třídu ServiceHost. ServiceType: ' [typ] '.|Otevřít||  
|Z|Ukončete třídu ServiceHost. ServiceType: ' [typ] '.|Zavřít||  
|O|Naslouchat na ' [adresa] '.|ListenAt|Tato a další aktivita jsou specifické pro přenos. Aktivita ListenAt představuje obsah, který se mapuje na adresu, na které naslouchá naslouchací proces kanálu. V případě služby MSMQ se jedná o vlastní frontu, protože fronta je mapována na jednu adresu. Tato aktivita naslouchá pro příchozí připojení v případě přenosů orientovaných na připojení pro zprávy služby MSMQ v případě služby MSMQ. Tato aktivita se vytvoří během procesu ServiceHost. Open () a obsahuje trasování týkající se vytváření a likvidace naslouchacího procesu a také pro přenos všech ReceiveBytes aktivit.|  
|P|Přijaté bajty v připojení [adresa] Přijmout zprávu služby MSMQ.|ReceiveBytes|V této aktivitě se zpracují data, která nakonec obdrží zprávu WCF. Příchozí bajty jsou v případě přenosu orientovaného na připojení nebo protokolu HTTP očekávány. V případě protokolu TCP/Named Pipe je doba života této aktivity životností připojení, jak je vytvořena při vytvoření připojení. V případě protokolu HTTP se jedná o životnost žádosti o zprávu, která se vytvoří při odeslání zprávy. Tato aktivita obsahuje trasování související s vytvořením a zrušením připojení, pokud je to možné, a také převádí na všechny aktivity zpracování zpráv (objektů).<br /><br /> V případě služby MSMQ je to aktivita, kde je načtena zpráva služby MSMQ.|  
|Q|Zpráva procesu [číslo]. (Poznámka: [číslo] je rovnoměrně zvětšující rostoucí hodnota, která začíná na 1.)|ProcessMessage|Zpracuje příchozí zprávu. Tato aktivita se spustí, když budou přijata všechna data (bajty, zpráva MSMQ) pro vytvoření objektu zprávy WCF. Trasování v rámci této aktivity se zabývat hlavičkou.<br /><br /> Jakmile se vytvoří zpráva, která se dá odeslat, po vyhledání příslušného ID aktivity se Aktivita ProcessAction ServiceHost přepne na.|  
|D, S|Akce procesu [Action].|ProcessAction|Zpracuje zprávu prostřednictvím zásobníku Transport/Security/RM pro odeslání zprávy do uživatelského kódu při přijetí a v obráceném pořadí při odeslání.<br /><br /> Na serveru tato aktivita používá šířené ID aktivity, pokud je odesílána v hlavičce zprávy prostřednictvím "šíření aktivity"; v opačném případě se vytvoří nový identifikátor GUID.<br /><br /> V této aktivitě je také zpracována zpráva odpovědi pro kontrakty požadavků a odpovědí.|  
|T|Spusťte operaci [IContract. Operation].|ExecuteUserCode|Po odeslání na straně služby spusťte kód uživatele. Tato aktivita poskytuje hranici pro odděluje kód ServiceHost od uživatelsky zadaného kódu.|  
  
## <a name="security-activities"></a>Aktivity zabezpečení  
 V následující tabulce jsou uvedeny všechny aktivity související se zabezpečením.  
  
|Název aktivity|Typ aktivity|Popis|  
|-------------------|-------------------|-----------------|  
|Nastavit zabezpečenou relaci|SetupSecurity|Existuje pouze na straně klienta. Obsahuje všechny výměny RST */SCT pro ověřování a nastavení kontextu zabezpečení. Pokud `propagateActivity` = `true` je tato aktivita sloučena s odpovídající akcí procesu RST \* /SCT aktivit služby.|  
|Zavřít zabezpečenou relaci|SetupSecurity|Existuje na straně klienta. Obsahuje výměnu zpráv zrušením pro zavření zabezpečené relace. Pokud `propagateActivity` = `true` je tato aktivita sloučena s akcí procesu "Cancel" ze služby.|  
  
 V následující tabulce jsou uvedeny všechny aktivity týkající se modelu COM+.  
  
|Název aktivity|Typ aktivity|Popis|  
|-------------------|-------------------|-----------------|  
|Vytvořit instanci COM+|TransferToCOMPlus|1 instance aktivity pro každé volání COM+ z kódu WCF|  
|Spustit COM+\<operation>|TransferToCOMPlus|1 instance aktivity pro každé volání COM+ z kódu WCF|  
  
## <a name="wmi-activities"></a>Aktivity rozhraní WMI  
 V následující tabulce jsou uvedeny všechny aktivity související s rozhraním WMI.  
  
|Název aktivity|Typ aktivity|Popis|  
|-------------------|-------------------|-----------------|  
|Rozhraní WMI Get|WMIGetObject|Uživatel načítá data z rozhraní WMI.|  
|Rozhraní WMI Put|WmiPutInstance|Uživatel aktualizuje data pomocí rozhraní WMI.|
