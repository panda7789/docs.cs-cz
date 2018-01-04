---
title: "Použití monikeru služby WCF u klientů modelu COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dbda85f056d7e8a465127bff948dcaaaf41094d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>Použití monikeru služby WCF u klientů modelu COM
Tento příklad znázorňuje způsob použití [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] monikeru služby pro integraci webových služeb do založená na modelu COM vývojových prostředí, jako je například Microsoft Office Visual Basic pro aplikace (Office VBA) nebo Visual Basic 6.0. Tato ukázka se skládá z klienta Windows Script Host (.vbs), podporující klientské knihovny DLL (.dll) a služby knihovny (DLL) hostované Internetové informační služby (IIS). Služba je služba kalkulačky a klient COM volá matematické operace – přidat, odečíst, násobit a dělit – ve službě. Činnost klienta je viditelný v systému windows pole zpráva.  
  
> [!NOTE]
>  Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 Implementuje služby `ICalculator` kontrakt definovaný jak je znázorněno v následujícím příkladu kódu.  
  
```  
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
  
 Ukázka ukazuje tři alternativní přístupy k použití Přezdívka:  
  
-   Typové kontrakt – kontrakt je registrován jako typ viditelné modelu COM v klientském počítači.  
  
-   Kontrakt WSDL – kontrakt poskytuje ve formě dokumentu WSDL.  
  
-   V době běhu z koncového bodu metadat Exchange (MEX) je načíst metadata Exchange kontrakt – kontrakt.  
  
## <a name="typed-contract"></a>Typové kontraktu  
 Pokud chcete použít Přezdívka s použitím zadaných kontrakt, musí být správně s atributy typy pro kontrakt služby registrovaný pomocí modelu COM. Nejprve klienta musí být vytvořen pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Spusťte následující příkaz z příkazového řádku v adresáři klienta ke generování typem proxy.  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Tato třída musí být součástí projekt a projekt by měl být nakonfigurovaný pro generování COM – viditelné, podepsané sestavení při kompilaci. Následující atribut by měl být součástí souboru AssemblyInfo.cs.  
  
```  
[assembly: ComVisible(true)]  
```  
  
 Po vytvoření projektu, zaregistrujte COM – viditelné typy pomocí `regasm` jak je znázorněno v následujícím příkladu.  
  
```  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 Sestavení, které se vytvoří musí být přidaní do globální mezipaměti sestavení. I když není nezbytně nutné, tato funkce zjednodušuje proces modulu runtime vyhledání sestavení. Následující příkaz přidá sestavení do globální mezipaměti sestavení.  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  Monikeru služby vyžaduje pouze registrace typu a nepoužívá ke komunikaci se službou proxy serveru.  
  
 ComCalcClient.vbs klientská aplikace používá `GetObject` funkce sestavit proxy server pro službu pomocí syntaxe přezdívka služby zadáním adresy, vazby a smlouvy pro službu.  
  
```  
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Zadejte parametry používané Přezdívka:  
  
-   Adresa koncového bodu služby.  
  
-   Vazba, který klient musí použít pro připojení k tohoto koncového bodu. V takovém případě wsHttpBinding definované v systému se používá, když vlastní vazby lze definovat v konfiguračních souborech klienta. Pro použití se službou Windows Script Host vlastní vazby je definována v souboru Cscript.exe.config ve stejném adresáři jako Cscript.exe.  
  
-   Typ smlouvy, které je podporovaná v koncový bod. Jedná se o typ, která byla vygenerována a zaregistrován výše. Vzhledem k tomu, že skript jazyka Visual Basic neposkytuje prostředí silného typu modelu COM, musí být zadán identifikátor pro kontrakt. Tento identifikátor GUID je `interfaceID` z CalcProxy.tlb, které lze zobrazit pomocí nástrojů modelu COM, jako je například prohlížeč objektů OLE/COM (OleView.exe). Silně typované prostředích, jako je Office VBA nebo Visual Basic 6.0 přidávání explicitní odkaz na typ knihovny a potom deklarující typ objektu proxy použít místo parametr kontrakt. To také poskytuje podporu technologie IntelliSense během vývoje aplikace klienta.  
  
 S vytvořená instance proxy s monikeru služby, klientská aplikace můžete volat metody pro proxy server, což vede k volání odpovídající operací služby infrastruktury přezdívka služby.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Při spuštění vzorového odpověď operace se zobrazí v okně Windows Script Host zprávy. Tento příklad ukazuje volání modelu COM pomocí zadaných Přezdívka ke komunikaci s klient COM [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. Bez ohledu na použití modelu COM v aplikaci klienta komunikace se službou se skládá jenom z volání webové služby.  
  
## <a name="wsdl-contract"></a>Kontraktů WSDL  
 Používat Přezdívka kontraktu WSDL, není požadována žádná registrace knihovny klienta, ale WSDL kontrakt služby musí být načteny prostřednictvím mechanismus out-of-band například pomocí prohlížeče přístup WSDL koncový bod pro službu. Přezdívka můžete poté přistoupit v době provádění tohoto kontraktu.  
  
 Klientská aplikace ComCalcClient.vbs používá `FileSystemObject` pro přístup k souboru WSDL místně uložené a pak znovu použije `GetObject` funkce vytvořit proxy server pro službu.  
  
```  
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
  
 Zadejte parametry používané Přezdívka:  
  
-   Adresa koncového bodu služby.  
  
-   Vazba, který klient musí použít pro připojení k tohoto koncového bodu a obor názvů, ve kterém je definovaný vazbou. V takovém případě `wsHttpBinding_ICalculator` se používá.  
  
-   WSDL, který definuje kontrakt. V takovém případě je řetězec, který byl přečten ze souboru serviceWsdl.xml.  
  
-   Název a obor názvů kontraktu. Toto identifikační není nutná, protože schématu WSDL může obsahovat více než jeden kontrakt.  
  
    > [!NOTE]
    >  Ve výchozím nastavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby generovat samostatné soubory WSDL pro každý obor názvů, použití. Tyto jsou propojeny s použitím konstrukce import schématu WSDL. Protože moniker se očekává jenom jednu definici WSDL, službu buď musíte použít jeden obor názvů, jak je předvedeno v této ukázce nebo samostatné soubory je potřeba ručně sloučit.  
  
 S vytvořená instance proxy s monikeru služby, klientská aplikace můžete volat metody pro proxy server, což vede k volání odpovídající operací služby infrastruktury přezdívka služby.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Při spuštění vzorového odpověď operace se zobrazí v okně Windows Script Host zprávy. Tento příklad ukazuje volání modelu COM pomocí Přezdívka kontraktu WSDL ke komunikaci s klient COM [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
## <a name="metadata-exchange-contract"></a>Metadata Exchange kontraktu  
 Pokud chcete používat Přezdívka s MEX kontraktu, stejně jako u kontraktů WSDL, není požadována žádná registrace klienta. V době provedení prostřednictvím interní použití systému Metadata Exchange se načítají, kontrakt služby.  
  
 Klientská aplikace ComCalcClient.vbs znovu používá `GetObject` funkce vytvořit proxy server pro službu.  
  
```  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Zadejte parametry používané Přezdívka:  
  
-   Adresa koncového bodu služby metadata exchange.  
  
-   Adresa koncového bodu služby.  
  
-   Vazba, který klient musí použít pro připojení k tohoto koncového bodu a obor názvů, ve kterém je definovaný vazbou. V takovém případě `wsHttpBinding_ICalculator` se používá.  
  
-   Název a obor názvů kontraktu. Toto identifikační není nutná, protože schématu WSDL může obsahovat více než jeden kontrakt.  
  
 S vytvořená instance proxy s monikeru služby, klientská aplikace můžete volat metody pro proxy server, což vede k volání odpovídající operací služby infrastruktury přezdívka služby.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Při spuštění vzorového odpověď operace se zobrazí v okně Windows Script Host zprávy. Tento příklad ukazuje volání modelu COM pomocí Přezdívka kontraktu MEX ke komunikaci s klient COM [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Jak nastavit a sestavit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Z [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] příkazový řádek, otevřete složku \client\bin, ve složce konkrétní jazyk.  
  
    > [!NOTE]
    >  Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 nebo Windows Server 2008 R2, ujistěte se, spuštění příkazového řádku s oprávněními správce.  
  
4.  Zadejte `tlbexp.exe client.dll /out:CalcProxy.tlb` Export knihovny dll tlb souboru. "Typ upozornění – Exportér knihovny" je očekávána, ale není problém, protože obecného typu se nevyžaduje.  
  
5.  Zadejte `regasm.exe /tlb:CalcProxy.tlb client.dll` typy zaregistrovat u modelu COM. "Typ upozornění – Exportér knihovny" je očekávána, ale není problém, protože obecného typu se nevyžaduje.  
  
6.  Zadejte `gacutil.exe /i client.dll` přidat sestavení do globální mezipaměti sestavení.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Test, který jste mají přístup ke službě pomocí prohlížeče zadáním v následující adrese: `http://localhost/servicemodelsamples/service.svc`. Potvrzovací stránku má být zobrazena v odpovědi.  
  
2.  Spusťte ComCalcClient.vbs z \client získáte složky pro konkrétní jazyk. Činnost klienta se zobrazí ve windows pole zpráva.  
  
3.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Na počítači se službou vytvořte virtuální adresář s názvem ServiceModelSamples. Skript Setupvroot.bat součástí vzorku lze použít k vytvoření adresáře disk a virtuální adresář.  
  
2.  Zkopírujte soubory programu služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do ServiceModelSamples virtuálního adresáře na počítači se službou. Nezapomeňte zahrnout soubory v adresáři \bin.  
  
3.  Zkopírujte soubor skriptu klienta ve složce \client ve složce jazyka na klientský počítač.  
  
4.  V souboru skriptu změňte hodnotu adresu definice koncového bodu tak, aby odpovídala nové adresy vaší služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.  
  
5.  Zkopírujte soubor WSDL do klientského počítače. V souboru WSDL serviceWsdl.xml, nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.  
  
6.  Kopírování knihovně Client.dll ve složce \client\bin ve složce pro specifický jazyk do jiného adresáře v klientském počítači.  
  
7.  Z příkazového řádku přejděte do adresáře cílové v klientském počítači. Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nezapomeňte příkazový řádek spustit jako správce.  
  
8.  Zadejte `tlbexp.exe client.dll /out:CalcProxy.tlb` Export knihovny dll tlb souboru. "Typ upozornění – Exportér knihovny" je očekávána, ale není problém, protože obecného typu se nevyžaduje.  
  
9. Zadejte `regasm.exe /tlb:CalcProxy.tlb client.dll` typy zaregistrovat u modelu COM. Ujistěte se, zda cesta byla nastavena na složku, která obsahuje `regasm.exe` před spuštěním příkazu.  
  
10. Zadejte `gacutil.exe /i client.dll` přidat sestavení do globální mezipaměti sestavení. Ujistěte se, zda cesta byla nastavena na složku, která obsahuje `gacutil.exe` před spuštěním příkazu.  
  
11. Test službě můžete dostat z klientského počítače pomocí prohlížeče.  
  
12. Na klientském počítači spusťte ComCalcClient.vbs.  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
-   Z bezpečnostních důvodů odeberte definici virtuální adresář a oprávnění udělená v průběhu instalace, když skončíte s ukázky.  
  
## <a name="see-also"></a>Viz také
