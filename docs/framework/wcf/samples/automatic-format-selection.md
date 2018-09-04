---
title: Automatický výběr formátu
ms.date: 03/30/2017
ms.assetid: dab51e56-8517-4a6a-bb54-b55b15ab37bb
ms.openlocfilehash: 4fd695195f5c7c13bc088248a6b3c12388328d37
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659758"
---
# <a name="automatic-format-selection"></a>Automatický výběr formátu
Tento příklad ukazuje, jak povolit automatický výběr formátu (XML nebo JSON) pomocí služby Windows Communication Foundation (WCF) REST programovací model, jakož i jak explicitně nastavit formát v kódu operace.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Ukázka se skládá z služby spolu s klientský kód, který se vytvářejí požadavky na službu. Tato služba podporuje jeden HTTP `GET` operace (`EchoWithGet`) a jeden HTTP `POST` operace (`EchoWithPost`). Operace očekávat řetězec a pak se vraťte řetězec v odpovědi. S `GET` operace, řetězec je k dispozici v parametru řetězce dotazu URI. S `POST` operace, řetězec je k dispozici v textu požadavku, serializovanou ve formátu XML. Služba se bude moct vrátit odpovědi v XML nebo JSON, využívající novou automatický výběr formátu a imperativního formát výběru funkcí v [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
 V ukázce je povolen automatický výběr formátu pomocí souboru App.config. Na výchozí koncový bod webových služeb HTTP `automaticFormatSelectionEnabled` atribut nebyla zadána hodnota `true`. Automatický výběr formátu povolené infrastruktura WCF vybrány nejvhodnější formát odpovědi (XML nebo JSON) uvedené hlavičky HTTP přijmout nebo Content-Type žádosti. Vývojář se musí provést žádné další kód nebo než nastavení konfigurace `automaticFormatSelectionEnabled` atribut `true` pro použití této nové funkce. V klientském kódu v souboru Program.cs, odešlou požadavky na obojí `GET` a `POST` operace služby s hlavičku HTTP přijmout zadaný jako "application/xml" nebo "application/json" a vrátí odpověď, která odpovídající formát.  
  
 Také v `GET` operace, imperativní formát výběru se používá. `GET` Operace zkontroluje volitelně `format` parametr s řetězcem dotazu a pokud jsou k dispozici, nastaví formát odpovědi na <xref:System.ServiceModel.Web.WebOperationContext.OutgoingResponse%2A> vlastnost. Výběr automatického formátu provádí infrastruktura WCF imperativně nastavení formát odpovědi tímto způsobem přepíše.  
  
 Ukázka se skládá z služba v místním prostředí a klienta, který běží v rámci konzolové aplikace. Konzolová aplikace běží, klient vytvářejí požadavky na službu a zapíše relevantní informace z odpovědi v okně konzoly.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení pro ukázku výběr automatického formátu. Při spuštění [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], musíte spustit jako správce pro ukázku proběhl úspěšně. To můžete provést kliknutím pravým tlačítkem myši [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonu a vyberte **spustit jako správce** v místní nabídce.  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, sestavte řešení a pak stisknutím kombinace kláves Ctrl + F5 spusťte AutomaticFormatSelection projekt konzolové aplikace. V okně konzoly se zobrazí a poskytuje URI spuštěnou službu a stránku pro spuštěnou službu identifikátoru URI HTML s nápovědou.  
  
3.  Při spuštění ukázky, klient zasílá požadavky službě a zapíše odpovědi v okně konzoly. Všimněte si různých formátech odpovědi v XML a JSON.  
  
4.  Stisknutím libovolné klávesy ukončete vzorovou.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AutomaticFormatSelection`  
  
## <a name="see-also"></a>Viz také
