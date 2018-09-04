---
title: Rozšířený výběr formátu
ms.date: 03/30/2017
ms.assetid: e02d9082-4d55-41d8-9329-98f6d1c77f06
ms.openlocfilehash: e5c396ce22e9021d453a70f3826b0bd3cc6aaf42
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43535087"
---
# <a name="advanced-format-selection"></a>Rozšířený výběr formátu
Tato ukázka předvádí, jak rozšířit programovací model REST Windows Communication Foundation (WCF) pro podporu nové odchozí odpovědi formáty. Kromě toho Ukázka používá k vrácení odpovědi jako stránku XHTML předvede, jak je možné implementovat programovací model styl zobrazení šablony T4.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Ukázka se skládá z jednoduchého služby spolu s klientský kód, který se vytvářejí požadavky na službu.  Tato služba podporuje jednu operaci [WebGet], který má následující podpis metody: `Message EchoListWithGet(string list);`  
  
 Když klient odešle požadavek na službu, nabízí čárkou oddělený seznam položek z `list` parametr s řetězcem dotazu a služba vrátí tento stejný seznam v jednom z následujících formátů: XML, JSON, Atom, XHTML nebo jpeg.  
  
 Formát odpovědi vrácené službou první závisí `format` parametr s řetězcem dotazu a sekundu, které hlavičky protokolu HTTP přijmout zadaný v požadavku. Pokud hodnota `format` parametr řetězce dotazu je jeden z předchozích formátů a pak odpověď se vrátí v tomto formátu. Pokud `format` řetězec dotazu není k dispozici, pak služba iteruje skrz prvky hlavičky Accept z požadavku a vrátí formát první typ obsahu, který podporuje službu.  
  
 Návratový typ operace je vhodné poznamenat. Pouze nativní programovací model REST WCF podporuje formáty odpovědi XML a JSON při operaci vrací typ jiný než <xref:System.ServiceModel.Channels.Message>. Ale při použití <xref:System.ServiceModel.Channels.Message> jako návratový typ, vývojář má úplnou kontrolu nad formátování obsah zprávy.  
  
 Ukázka používá <xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A>, <xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> a <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> metody k serializaci seznam řetězců, které do zprávy XML, JSON a ATOM v uvedeném pořadí. Pro formát odpovědi jpeg <xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> metoda se používá a obrázku se uloží do datového proudu. Pro odpověď v XHTML <xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> se používá spolu s předzpracovaná šablona T4, který se skládá z .tt soubor a soubor automaticky generované .cs. Soubor .tt umožňuje vývojáři psát odpovědi ve formě šablony, který obsahuje proměnné a řídit struktury. Další informace o šablonách T4 naleznete v tématu [generování artefakty podle pomocí textových šablon](https://go.microsoft.com/fwlink/?LinkId=166023).  
  
 Ukázka se skládá z služba v místním prostředí a klienta, který běží v rámci konzolové aplikace. Konzolová aplikace běží, klient vytvářejí požadavky na službu a zapíše relevantní informace z odpovědi v okně konzoly.  
  
#### <a name="to-run-this-sample"></a>Tuto ukázku spustit  
  
1.  Otevřete řešení pro ukázku rozšířené formát výběru. Při spuštění [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], měli byste spustit jako správce pro ukázku proběhl úspěšně. To můžete provést kliknutím pravým tlačítkem myši [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonu a zvolíte **spustit jako správce** v místní nabídce.  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, sestavte řešení a pak stisknutím kombinace kláves Ctrl-F5 spusťte projekt konzolové aplikace AdvancedFormatSelection bez ladění. V okně konzoly se zobrazí a poskytuje URI spuštěnou službu a stránku pro spuštěnou službu identifikátoru URI HTML s nápovědou.  
  
3.  Při spuštění ukázky, klient zasílá požadavky službě a zapíše odpovědi v okně konzoly. Všimněte si různých formátech odpovědi: XML, JSON, Atom nebo XHTML.  
  
4.  Zobrazí se výzva k procházení k identifikátoru URI, ve kterém můžete požádat o odpověď ve formátu .jpeg. Otevřete prohlížeč a přejděte do daného identifikátoru URI.  
  
5.  Stisknutím libovolné klávesy ukončete vzorovou.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AdvancedFormatSelection`  
  
## <a name="see-also"></a>Viz také
