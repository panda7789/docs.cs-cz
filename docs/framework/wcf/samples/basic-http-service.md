---
title: Základní služba HTTP
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: 8dfcd5a751bcef6aa24b5cb4a200c8820c43fe81
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716092"
---
# <a name="basic-http-service"></a>Základní služba HTTP

Tato ukázka předvádí, jak implementovat službu RPC založenou na protokolu HTTP, která je oblíbená jako "POX" (obyčejná stará XML) – pomocí programovacího modelu REST služby Windows Communication Foundation (WCF). Tato ukázka se skládá ze dvou součástí: Samoobslužná služba WCF HTTP (Service.cs) a Konzolová aplikace (Program.cs), která vytvoří službu a provede na ni volání.

## <a name="sample-details"></a>Podrobnosti ukázky

Služba WCF zpřístupňuje 2 operace, `EchoWithGet` a `EchoWithPost`, což vrátí řetězec, který byl předán jako vstup.

Operace `EchoWithGet` je označena <xref:System.ServiceModel.Web.WebGetAttribute>, která indikuje, že operace zpracovává požadavky HTTP `GET`. Vzhledem k tomu, že <xref:System.ServiceModel.Web.WebGetAttribute> explicitně neurčuje <xref:System.UriTemplate>, operace očekává, že vstupní řetězec bude předán pomocí parametru řetězce dotazu s názvem `s`. Všimněte si, že formát identifikátoru URI, který služba očekává, lze přizpůsobit pomocí vlastnosti <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A>.

Operace `EchoWithPost` je Poznáma s <xref:System.ServiceModel.Web.WebInvokeAttribute>, což znamená, že se nejedná o operaci `GET` (má vedlejší účinky). Vzhledem k tomu, že <xref:System.ServiceModel.Web.WebInvokeAttribute> explicitně neurčuje `Method`, operace zpracovává požadavky HTTP `POST`, které mají řetězec v textu žádosti (například ve formátu XML, např.). Všimněte si, že metoda HTTP a formát identifikátoru URI pro požadavek lze přizpůsobit pomocí <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> a <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate>ch vlastností v uvedeném pořadí.

Soubor App. config konfiguruje službu WCF s výchozím <xref:System.ServiceModel.Description.WebHttpEndpoint>, která má vlastnost <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> nastavenou na `true`. V důsledku toho infrastruktura WCF vytvoří na `http://localhost:8000/Customers/help` stránku s automatickou podporou HTML, která poskytuje informace o tom, jak vytvořit požadavky HTTP ke službě a jak používat odpověď HTTP služby.

Program.cs ukazuje, jak lze pomocí objektu pro vytváření kanálů WCF volat služby a zpracovávat odpovědi. Všimněte si, že toto je pouze jeden způsob, jak získat přístup ke službě WCF. Ke službě je také možné přistupovat pomocí jiných tříd .NET Framework, jako je <xref:System.Net.HttpWebRequest> a <xref:System.Net.WebClient>.

Ukázka se skládá ze samoobslužné služby a klienta spouštěného v konzolové aplikaci. Při spuštění konzolové aplikace klient provede požadavky na službu a zapíše příslušné informace z odpovědí do okna konzoly.

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Otevřete řešení pro základní ukázku služby HTTP. Při spuštění sady Visual Studio 2012 musíte spustit jako správce, aby se vzorek úspěšně spustil. Provedete to tak, že kliknete pravým tlačítkem na ikonu Visual studia 2012 a v místní nabídce vyberete **Spustit jako správce** .

2. Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení a stisknutím kombinace kláves CTRL + F5 spusťte konzolovou aplikaci bez ladění. Zobrazí se okno konzoly, ve kterém je uveden identifikátor URI běžící služby a identifikátor URI stránky s nápovědu HTML pro běžící službu. V jakémkoli okamžiku můžete zobrazit stránku HTML Help zadáním identifikátoru URI stránky s nastavením v prohlížeči. Po spuštění ukázkového klienta zapíše klient stav aktuální aktivity.

3. Stisknutím libovolné klávesy ukončete ukázku.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`
