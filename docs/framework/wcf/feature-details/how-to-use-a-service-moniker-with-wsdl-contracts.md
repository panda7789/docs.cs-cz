---
title: 'Postupy: Použití monikeru služby u kontraktů WSDL'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 7bc628952d4a7198f0b5545014ae931bbf73dab3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969005"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a>Postupy: Použití monikeru služby u kontraktů WSDL
Existují situace, kdy možná budete chtít mít zcela samostatný klient zprostředkovatele komunikace s objekty COM. Služba, kterou chcete volat, nesmí vystavit koncový bod MEX a Klientská knihovna WCF nemusí být registrována pro zprostředkovatele komunikace s objekty COM. V těchto případech můžete vytvořit soubor WSDL, který popisuje službu a předává ji do monikeru služby WCF. Toto téma popisuje, jak volat ukázku Začínáme WCF pomocí monikeru WCF WSDL.  
  
### <a name="using-the-wsdl-service-moniker"></a>Použití monikeru služby WSDL  
  
1. Otevřete a sestavte ukázkové řešení soubor GettingStarted.  
  
2. Spusťte Internet Explorer a přejděte na `http://localhost/ServiceModelSamples/Service.svc` adresu a ujistěte se, že služba funguje.  
  
3. V souboru Service.cs přidejte následující atribut pro třídu CalculatorService:  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. Přidejte obor názvů vazby do App Service. config:  

5. Vytvořte soubor WSDL, který má aplikace číst. Vzhledem k tomu, že obory názvů byly přidány v krocích 3 a 4, můžete použít aplikaci IE k dotazování na celý popis služby WSDL `http://localhost/ServiceModelSamples/Service.svc?wsdl`, a to tak, že přejdete na. Pak můžete soubor uložit z aplikace Internet Explorer jako serviceWSDL. XML. Pokud neurčíte obory názvů v krocích 3 a 4, dokument WSDL vrácený z dotazu na výše uvedenou adresu URL nebude kompletní WSDL. Vrácený dokument WSDL bude obsahovat několik příkazů importu, které importují jiné dokumenty WSDL. Budete muset projít každým příkazem importu a sestavit kompletní dokument WSDL a kombinaci prvku WSDL vráceného z této služby s importovaným jazykem WSDL.  
  
6. Otevřete Visual Basic 6,0 a vytvořte nový standardní soubor. exe. Přidejte do formuláře tlačítko a dvakrát klikněte na tlačítko a přidejte následující kód do obslužné rutiny Click:  
  
    ```vb
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
    > Pokud je moniker poškozený nebo pokud není služba k dispozici, volání `GetObject` vrátí chybu s názvem neplatná syntaxe.  Pokud se zobrazí tato chyba, ujistěte se, že moniker, který používáte, je správný a služba je k dispozici.  
  
7. Spusťte aplikaci Visual Basic. Zobrazí se okno se zprávou s výsledky volání odečíst (145, 76,54).  
  
## <a name="see-also"></a>Viz také:

- [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Přehled integrace s aplikacemi modelu COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
