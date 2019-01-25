---
title: Odstraňování problémů v kurzu Začínáme
ms.date: 03/30/2017
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 5b8cd04ef4d98e522e255e1b7529e848351b2e0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695657"
---
# <a name="troubleshooting-the-getting-started-tutorial"></a>Odstraňování problémů v kurzu Začínáme
Toto téma uvádí nejběžnější problémy vzniklé při práci prostřednictvím kurzu Začínáme a způsob jejich řešení.  
  
**Nejde najít soubory projektu na pevném disku.**

 Visual Studio uloží soubory projektu v c:\users\\<user name>\Documents\\< verze sady Visual Studio\>\Projects.  
  
**Došlo k pokusu o spuštění služby aplikace: Protokol HTTP nemohl zaregistrovat adresu URL `http://+:8000/ServiceModelSamples/Service/`.** 
 **Váš proces nemá přístupová práva k tomuto oboru názvů.** 

 Proces, který hostuje službu WCF musí být spuštěn s oprávněním správce. Pokud používáte službu ze sady Visual Studio, musíte spustit aplikaci Visual Studio jako správce. Klepněte na tlačítko **Start**, klikněte pravým tlačítkem na **sady Visual Studio \< *verze* >**  a vyberte **spustit jako správce**. Pokud používáte službu z příkazového řádku v okně konzoly, musí v okně konzoly spusťte jako správce podobným způsobem. Klikněte na tlačítko **Start**, klikněte pravým tlačítkem na **příkazového řádku** a vyberte **spustit jako správce**.  
  
**Pokus o použití nástroje Svcutil.exe: 'svcutil' nebyl rozpoznán jako vnitřního ani vnějšího příkazu, spustitelného programu nebo dávkového souboru.**

 Svcutil.exe musí být v systémové cestě. Nejjednodušším řešením je použít příkazový řádek. Klikněte na tlačítko **Start**vyberte **všechny programy**, **sady Visual Studio \< *verze*>**,  **Nástroje sady Visual Studio**, a **Developer Command Prompt pro sadu Visual Studio**. Tento příkazový řádek nastaví systémové cesty na správné umístění pro všechny nástroje dodávané jako součást sady Visual Studio.  

**Nepovedlo se najít soubor App.config generovaných Svcutil.exe.**

 **Přidat existující položku** dialogové okno zobrazí ve výchozím nastavení pouze soubory s těmito příponami: .cs, .resx, .settings, XSD, WSDL. Můžete určit, že chcete zobrazit všechny typy souborů tak, že vyberete **všechny soubory (\*.\*)**  v rozevíracím seznamu v pravém dolním rohu **přidat existující položku** dialogové okno.  


**Kompilování klientská aplikace: 'CalculatorClient' neobsahuje definici pro '\<název metody > "a žádná metoda rozšíření '\<název metody >' přijímala první argument typu 'CalculatorClient' nebyla nalezena. (nechybí using – direktiva nebo odkaz na sestavení?)**  

Pouze těch metod, které jsou označené `ServiceOperationAttribute` jsou vystaveny vnějším světem. Pokud je vynechán `ServiceOperationAttribute` atribut z jedné z metod v `ICalculator` rozhraní, dostanete tuto chybovou zprávu při kompilaci klientskou aplikaci, která provádí volání na operaci chybí atribut.  

**Kompilování klientská aplikace: Typ nebo obor názvů 'CalculatorClient' nebyl nalezen. (nechybí using – direktiva nebo odkaz na sestavení?)**

 K této chybě získáte, pokud nepřidáte Proxy.cs nebo Proxy.vb soubor do projektu klienta.  

**Spuštění klienta: Neošetřená výjimka: System.ServiceModel.EndpointNotFoundException: Nelze se připojit k `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`. Kód chyby TCP 10061: Protože cílový počítač aktivně odmítl může nevytváří žádné připojení.**

K této chybě dochází, pokud spuštění klientské aplikace bez nutnosti spuštění služby.  
  
**Neošetřená výjimka: System.ServiceModel.Security.SecurityNegotiationException: Vyjednávání zabezpečení SOAP s `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` pro cíl `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` se nezdařilo**  

K této chybě dochází v počítači připojeném k doméně, která nemá připojení k síti. Připojení počítače k síti nebo vypnout zabezpečení klienta a služby. Pro službu upravte kód, který se vytvoří vazba WSHttpBinding takto.  
  
```csharp
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```

Pro klienta, změnit  **\<zabezpečení >** element v rámci  **\<vazby >** – element pro následující:  
  
```xml
<security mode="Node" />  
```  

## <a name="see-also"></a>Viz také:
- [Kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md)
- [Řešení problémů s WCF – úvodní příručka](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)
- [Řešení problémů s instalací](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
