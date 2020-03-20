---
title: Použití monikeru služby WCF u klientů modelu COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: d4d812c59a504f365eb3ad63ddd45ba5a66296e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183238"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>Použití monikeru služby WCF u klientů modelu COM
Tato ukázka ukazuje, jak používat zástupný název služby WCF (Windows Communication Foundation) k integraci webových služeb do vývojových prostředí založených na modelu COM, jako je například Microsoft Office Visual Basic for Applications (Office VBA) nebo Visual Basic 6.0. Tato ukázka se skládá z klienta Hostitele skriptů systému Windows (.vbs), podpůrné klientské knihovny (.dll) a knihovny služeb (.dll) hostované Internetovou informační službou (IIS). Služba je služba kalkulačky a klient COM volá matematické operace – Přidat, Odečíst, Násobit a Rozdělit – ve službě. Aktivita klienta je viditelná v oknech okna okna okna se zprávou.  
  
> [!NOTE]
> Postup nastavení a sestavení pokyny pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 Služba implementuje `ICalculator` smlouvu definovanou, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 Ukázka ukazuje tři alternativní přístupy pro použití zástupný název:  
  
- Zadaný kontrakt – Smlouva je registrována jako viditelný typ com v klientském počítači.  
  
- WSDL smlouva – Smlouva je dodávána ve formě dokumentu WSDL.  
  
- Kontrakt výměny metadat – Kontrakt je načten za běhu z koncového bodu Výměny metadat (MEX).  
  
## <a name="typed-contract"></a>Zadaný kontrakt  
 Chcete-li použít zástupný název s typem smlouvy použití, vhodně přiřazené typy pro servisní smlouvu musí být registrovány com. Nejprve musí být klient vygenerován pomocí [nástroje ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Spusťte následující příkaz z příkazového řádku v adresáři klienta a vygenerujte zadaný proxy server.  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Tato třída musí být zahrnuta do projektu a projekt by měl být nakonfigurován tak, aby při kompilaci generoval podepsané sestavení viditelné pro COM. Následující atribut by měl být zahrnut do souboru AssemblyInfo.cs.  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 Po sestavení projektu zaregistrujte typy viditelné `regasm` com pomocí, jak je znázorněno v následujícím příkladu.  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 Sestavení, které je vytvořeno by měl být přidán do globální mezipaměti sestavení. I když to není nezbytně nutné, zjednodušuje proces hledání sestavení za běhu. Následující příkaz přidá sestavení do globální mezipaměti sestavení.  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> Zástupné řešení služby vyžaduje pouze registraci typu a nepoužívá proxy server ke komunikaci se službou.  
  
 Klientská aplikace ComCalcClient.vbs používá `GetObject` tuto funkci k vytvoření proxy serveru pro službu pomocí syntaxe zástupného prvku služby k určení adresy, vazby a smlouvy pro službu.  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Parametry použité zástupný název určit:  
  
- Adresa koncového bodu služby.  
  
- Vazba, kterou by měl klient použít k připojení k tomuto koncovému bodu. V tomto případě se používá systémově definovaná wsHttpBinding i když vlastní vazby lze definovat v konfiguračních souborech klienta. Pro použití s hostitelem skriptů systému Windows je vlastní vazba definována v souboru Cscript.exe.config ve stejném adresáři jako Cscript.exe.  
  
- Typ smlouvy, která je podporována v koncovém bodě. Toto je typ, který byl vygenerován a registrován výše. Vzhledem k tomu, že skript jazyka visual basic neposkytuje prostředí COM silného typu, musí být zadán identifikátor smlouvy. Tento identifikátor GUID je `interfaceID` z CalcProxy.tlb, který lze zobrazit pomocí nástrojů COM, jako je například PROHLÍŽEČ OBJEKTŮ OLE/COM (OleView.exe). Pro prostředí silného typu, jako je například Office VBA nebo Visual Basic 6.0, přidání explicitní odkaz na knihovnu typů a pak deklarovat typ proxy objektu lze použít místo parametru smlouvy. To také poskytuje podporu IntelliSense během vývoje klientských aplikací.  
  
 Po vytvoření instance proxy s zástupným serverem služby může klientská aplikace volat metody na serveru proxy, což vede k tomu, že infrastruktura zástupných spoje služby volá odpovídající operace služby.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Při spuštění ukázky se odpověď operace zobrazí v okně okna se zprávou Hostitele skriptů systému Windows. To ukazuje klienta modelu COM volání modelu COM pomocí zástupný název zadali ke komunikaci se službou WCF. I přes použití com v klientské aplikaci, komunikace se službou se skládá pouze z volání webové služby.  
  
## <a name="wsdl-contract"></a>WSDL smlouva  
 Chcete-li použít zástupný název se smlouvou WSDL, není vyžadována žádná registrace knihovny klienta, ale wsdl smlouvy pro službu musí být načteny prostřednictvím mechanismu out-of-band, jako je například použití prohlížeče pro přístup ke koncovému bodu WSDL pro službu. Zástupné název pak přístup k této smlouvy v době provádění.  
  
 Klientská aplikace ComCalcClient.vbs `FileSystemObject` používá přístup k místně uloženému souboru `GetObject` WSDL a poté znovu používá funkci k vytvoření proxy serveru pro službu.  
  
```vbscript  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 Parametry použité zástupný název určit:  
  
- Adresa koncového bodu služby.  
  
- Vazba, kterou by měl klient použít k připojení k tomuto koncovému bodu a oboru názvů, ve kterém je tato vazba definována. V tomto případě `wsHttpBinding_ICalculator` se používá.  
  
- WSDL, který definuje smlouvy. V tomto případě se jedná o řetězec, který byl přečten ze souboru serviceWsdl.xml.  
  
- Název a obor názvů smlouvy. Tato identifikace je vyžadována, protože WSDL může obsahovat více než jednu smlouvu.  
  
    > [!NOTE]
    > Ve výchozím nastavení služby WCF generují samostatné soubory WSDL pro každý obor názvů, který používá. Ty jsou spojeny s použitím wsdl import konstrukce. Vzhledem k tomu, že zástupný název očekává jednu definici WSDL, musí služba buď použít jeden obor názvů, jak je znázorněno v této ukázce, nebo samostatné soubory musí být ručně sloučeny.  
  
 Po vytvoření instance proxy s zástupným serverem služby může klientská aplikace volat metody na serveru proxy, což vede k tomu, že infrastruktura zástupných spoje služby volá odpovídající operace služby.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Při spuštění ukázky se odpověď operace zobrazí v okně okna se zprávou Hostitele skriptů systému Windows. To ukazuje klienta MODELU COM volání modelu COM pomocí zástupný název se smlouvou WSDL pro komunikaci se službou WCF.  
  
## <a name="metadata-exchange-contract"></a>Smlouva o výměně metadat  
 Chcete-li použít zástupný název se smlouvou MEX, jako u smlouvy WSDL, není vyžadována žádná registrace klienta. Smlouva pro službu je načtena v době spuštění prostřednictvím interního použití výměny metadat.  
  
 Klientská aplikace ComCalcClient.vbs `GetObject` opět používá tuto funkci k vytvoření proxy serveru pro službu.  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Parametry použité zástupný název určit:  
  
- Adresa koncového bodu výměny metadat služby.  
  
- Adresa koncového bodu služby.  
  
- Vazba, kterou by měl klient použít k připojení k tomuto koncovému bodu a oboru názvů, ve kterém je tato vazba definována. V tomto případě `wsHttpBinding_ICalculator` se používá.  
  
- Název a obor názvů smlouvy. Tato identifikace je vyžadována, protože WSDL může obsahovat více než jednu smlouvu.  
  
 Po vytvoření instance proxy s zástupným serverem služby může klientská aplikace volat metody na serveru proxy, což vede k tomu, že infrastruktura zástupných spoje služby volá odpovídající operace služby.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Při spuštění ukázky se odpověď operace zobrazí v okně okna se zprávou Hostitele skriptů systému Windows. To ukazuje klienta modelu COM volání modelu COM pomocí zástupný název se smlouvou MEX pro komunikaci se službou WCF.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Na příkazovém řádku pro vývojáře sady Visual Studio otevřete složku \client\bin pod složkou specifickou pro daný jazyk.  
  
    > [!NOTE]
    > Používáte-li systém Windows Vista, Windows Server 2008, Windows 7 nebo Windows Server 2008 R2, zkontrolujte, zda je spuštěn příkazový řádek s oprávněními správce.  
  
4. Zadáním `tlbexp.exe client.dll /out:CalcProxy.tlb` zadejte, chcete-li exportovat dll do souboru tlb. "Upozornění vývozce knihovny typů" se očekává, ale není problém, protože obecný typ není vyžadován.  
  
5. Zadáním `regasm.exe /tlb:CalcProxy.tlb client.dll` zadejte, chcete-li zaregistrovat typy pomocí com. "Upozornění vývozce knihovny typů" se očekává, ale není problém, protože obecný typ není vyžadován.  
  
6. Zadáním `gacutil.exe /i client.dll` do pole přidáte sestavení do globální mezipaměti sestavení.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky ve stejném počítači  
  
1. Otestujte, zda máte ke službě přístup pomocí prohlížeče, zadáním následující adresy: `http://localhost/servicemodelsamples/service.svc`. V reakci na to by měla být zobrazena stránka s potvrzením.  
  
2. Spusťte soubor ComCalcClient.vbs z \client z pod složky specifické pro jazyk. Aktivita klienta se zobrazí v oknech okna okna okna se zprávou.  
  
3. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky v počítačích  
  
1. V počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples. Skript Setupvroot.bat, který je součástí ukázky, lze použít k vytvoření adresáře disku a virtuálního adresáře.  
  
2. Zkopírujte soubory programu služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do virtuálního adresáře ServiceModelSamples v počítači služby. Nezapomeňte zahrnout soubory do adresáře \bin.  
  
3. Zkopírujte soubor klientského skriptu ze složky \client pod složkou specifickou pro daný jazyk do klientského počítače.  
  
4. V souboru skriptu změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.  
  
5. Zkopírujte soubor WSDL do klientského počítače. V souboru WSDL serviceWsdl.xml nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.  
  
6. Zkopírujte knihovnu Client.dll ze složky \client\bin pod stolicí specifickou pro daný jazyk do adresáře v klientském počítači.  
  
7. Z příkazového řádku přejděte do cílového adresáře v klientském počítači. Pokud používáte systém Windows Vista nebo Windows Server 2008, nezapomeňte spustit příkazový řádek jako správce.  
  
8. Zadáním `tlbexp.exe client.dll /out:CalcProxy.tlb` zadejte, chcete-li exportovat dll do souboru tlb. "Upozornění vývozce knihovny typů" se očekává, ale není problém, protože obecný typ není vyžadován.  
  
9. Zadáním `regasm.exe /tlb:CalcProxy.tlb client.dll` zadejte, chcete-li zaregistrovat typy pomocí com. Před spuštěním příkazu se ujistěte, že cesta byla nastavena na složku, která obsahuje. `regasm.exe`  
  
10. Zadáním `gacutil.exe /i client.dll` do pole přidáte sestavení do globální mezipaměti sestavení. Před spuštěním příkazu se ujistěte, že cesta byla nastavena na složku, která obsahuje. `gacutil.exe`  
  
11. Otestujte, zda máte přístup ke službě z klientského počítače pomocí prohlížeče.  
  
12. V klientském počítači spusťte soubor ComCalcClient.vbs.  
  
#### <a name="to-clean-up-after-the-sample"></a>Chcete-li vyčistit po vzorku  
  
- Z bezpečnostních důvodů odeberte definici virtuálního adresáře a oprávnění udělená v krocích nastavení po dokončení ukázek.  
