---
title: 'Postupy: Použití monikeru služby u kontraktů WSDL'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 2968641538bf0b4d0e136d5784bf69e5e7fcb3a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972884"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a>Postupy: Použití monikeru služby u kontraktů WSDL
Pokud chcete úplně nezávislý klient komunikace s objekty COM, existují situace. Na službu, kterou chcete volat nesmí zveřejnit koncový bod MEX a klientský WCF pro spolupráci s COM nelze registrovat knihovnu DLL. V těchto případech můžete vytvořit soubor WSDL, který popisuje službu a předejte ho do monikeru služby WCF. Toto téma popisuje, jak volat získávání WCF spustit ukázku pomocí monikeru WCF WSDL.  
  
### <a name="using-the-wsdl-service-moniker"></a>Použití monikeru služby WSDL  
  
1. Otevřít a sestavit GettingStarted ukázkové řešení.  
  
2. Spusťte aplikaci Internet Explorer a přejděte do `http://localhost/ServiceModelSamples/Service.svc` abyste měli jistotu, služba funguje.  
  
3. V souboru Service.cs přidejte následující atribut ve třídě CalculatorService:  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. Přidáte obor názvů vazby ve službě App.config:  

5. Vytvoření souboru WSDL pro aplikace pro čtení. Protože obory názvů byly přidány v krocích 3 a 4, můžete použít Internet Exploreru se dotázat na celý popis WSDL služby tak, že přejdete do `http://localhost/ServiceModelSamples/Service.svc?wsdl`. Potom můžete uložit soubor z aplikace Internet Explorer jako serviceWSDL.xml. Pokud nezadáte obory názvů v krocích 3 a 4, nebudou dokumentu WSDL vrácená z dotazu výše zobrazenou adresu URL dokončení WSDL. Dokument WSDL vrátil bude obsahovat několik příkazy pro import, které importují jiné dokumenty WSDL. Budete muset projít každý příkaz import a sestavit kompletní dokumentu WSDL, kombinování WSDL vrácený službou WSDL importovat.  
  
6. Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe. Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko Přidat následující kód do obslužné rutiny kliknutí:  
  
    ```  
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    >  Pokud je moniker je poškozený nebo pokud služba není k dispozici volání `GetObject` vrátí chyba s oznámením "Neplatná syntaxe".  Pokud se zobrazí tato chyba, ujistěte se, že zástupný název, který používáte, je správná a služba není k dispozici.  
  
7. Spuštění aplikace Visual Basic. Zobrazí se okno se zprávou s výsledky volání odečíst (145, 76.54).  
  
## <a name="see-also"></a>Viz také:

- [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Přehled integrace s aplikacemi modelu COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
