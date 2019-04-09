---
title: Použití monikeru služby WCF u klientů modelu COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 3cb610f85c929c371299bc505646cdf924ecdaea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098127"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>Použití monikeru služby WCF u klientů modelu COM
Tato ukázka demonstruje použití monikeru služby Windows Communication Foundation (WCF) k integraci webové služby do založené na modelu COM. vývojových prostředích, jako je například Microsoft Office Visual Basic for Applications (Office VBA) nebo Visual Basic 6.0. Tento příklad se skládá z klienta Windows Script Host (VBS), podpůrné klientské knihovny (DLL) a služby knihovny (.dll) hostované v Internetové informační služby (IIS). Služba je služba kalkulačky a klient modelu COM zavolá matematických operací – přidat, odečítání, násobení a rozdělit – ve službě. Činnost klienta je viditelný v ovládacím prvku windows pole zpráv.  
  
> [!NOTE]
>  Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 Implementuje služby `ICalculator` kontrakt definovaný, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Vzorek ukazuje tři alternativní přístupy k použití monikeru:  
  
-   Typu kontraktu – smlouvy je registrován jako typ viditelné modelu COM v klientském počítači.  
  
-   Smlouva WSDL – smlouvy se dodává ve formě dokument WSDL.  
  
-   Kontraktů výměny metadat – smlouvy je načten v době běhu z koncového bodu metadat Exchange (MEX).  
  
## <a name="typed-contract"></a>Typu kontraktu  
 Používat zástupný název typu kontraktu použití, musí být zaregistrovaný s odpovídajícím způsobem atributy typy pro kontrakt služby s modelu COM. Klient nejprve musí být generovány pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Spusťte následující příkaz z příkazového řádku v adresáři klienta ke generování typové proxy.  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Tato třída musí být součástí projektu a projekt by měl být nakonfigurovaný pro generování viditelný modulem COM, podepsané sestavení při kompilaci. Tento atribut by měl být zahrnuty v souboru AssemblyInfo.cs.  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 Po vytvoření projektu, zaregistrujte typ viditelný modulem COM s použitím `regasm` jak je znázorněno v následujícím příkladu.  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 Sestavení, který je vytvořen, měli byste přidat do globální mezipaměti sestavení. I když není nezbytně nutné, tato funkce zjednodušuje proces hledání sestavení modulu runtime. Následující příkaz přidá sestavení do globální mezipaměti sestavení.  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  Moniker služby vyžaduje pouze registrace typu a nepoužívá ke komunikaci se službou proxy serveru.  
  
 ComCalcClient.vbs klientská aplikace používá `GetObject` funkce proxy serveru pro službu, pomocí syntaxe moniker služby zadáním adresy, vazby, sestavit a kontrakt služby.  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Zadejte parametry používané zástupný název:  
  
-   Adresa koncového bodu služby.  
  
-   Vazby, který klient musí použít pro připojení pomocí tohoto koncového bodu. V takovém případě wsHttpBinding definované v systému se používá, i když je možné definovat vlastní vazby v konfiguračních souborů klienta. Pro použití s Windows Script Host je vlastní vazby definované v souboru Cscript.exe.config ve stejném adresáři jako Cscript.exe.  
  
-   Typ smlouvy, která je podporována v koncovém bodě. Jedná se o typ, který byl generován a zaregistrován výše. Vzhledem k tomu, že skript jazyka Visual Basic neposkytuje prostředí modelu COM silného typu, je třeba zadat identifikátor pro kontrakt. Tento identifikátor GUID je `interfaceID` z CalcProxy.tlb, které lze zobrazit pomocí nástroje modelu COM, jako je například prohlížeč objektů OLE/COM (OleView.exe). Silný prostředích, jako například Office VBA nebo Visual Basic 6.0 přidat explicitní odkaz na knihovnu typů a pak deklarační typ objektu proxy použít místo parametru kontraktu. To také poskytuje podporu technologie IntelliSense při vývoji klientských aplikací.  
  
 Instance proxy s monikeru služby s vytvořen, klientská aplikace může volat metody na proxy serveru, což vede k infrastruktuře moniker služby volání odpovídající operace služby.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Při spuštění ukázky v reakci na operaci se zobrazí v okně Windows Script Host zprávy. Tento příklad ukazuje klient modelu COM, volání modelu COM pomocí zadaný moniker komunikovat se službou WCF. Komunikace se službou se skládá pouze z volání webové služby bez ohledu na použití modelu COM v klientské aplikaci.  
  
## <a name="wsdl-contract"></a>Kontraktů WSDL  
 Používat zástupný název kontraktu WSDL, není požadována žádná registrace knihovny klienta ale WSDL kontrakt služby musí být načten mechanismem out-of-band jako je například přístup ke koncovému bodu WSDL pro službu pomocí prohlížeče. Zástupný název mohlo dostat přístup k této smlouvy v době spuštění.  
  
 Klientská aplikace ComCalcClient.vbs používá `FileSystemObject` pro přístup k místně uloženého souboru WSDL a pak znovu použije `GetObject` funkce k vytvoření proxy serveru pro službu.  
  
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
  
 Zadejte parametry používané zástupný název:  
  
-   Adresa koncového bodu služby.  
  
-   Vazby, který klient musí použít pro připojení pomocí tohoto koncového bodu a obor názvů, ve kterém je definován, že vazba. V takovém případě `wsHttpBinding_ICalculator` se používá.  
  
-   WSDL, který definuje kontrakt. V tomto případě je řetězec, který byl přečten ze souboru serviceWsdl.xml.  
  
-   Název a obor názvů kontraktu. Tato identifikace totiž jazyka WSDL může obsahovat více než jeden kontrakt.  
  
    > [!NOTE]
    >  Ve výchozím nastavení, služby WCF generovat samostatné soubory WSDL pro každý obor názvů, který používá. Tyto jsou propojeny s použitím konstrukce importu WSDL. Protože je moniker očekává jenom jednu definici WSDL, službu buď musí používat jednoho oboru názvů, jak je ukázáno v tomto příkladu nebo samostatné soubory je potřeba sloučit ručně.  
  
 Instance proxy s monikeru služby s vytvořen, klientská aplikace může volat metody na proxy serveru, což vede k infrastruktuře moniker služby volání odpovídající operace služby.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Při spuštění ukázky v reakci na operaci se zobrazí v okně Windows Script Host zprávy. Tento příklad ukazuje klient modelu COM, volání COM použití monikeru u kontraktů WSDL komunikovat se službou WCF.  
  
## <a name="metadata-exchange-contract"></a>Kontraktů Metadata Exchange  
 Pokud chcete použít zástupný název s kontraktem MEX, stejně jako u kontraktů WSDL, není požadována žádná registrace klienta. Kontrakt služby je načten v době provádění prostřednictvím interní použití výměny metadat.  
  
 Klientská aplikace ComCalcClient.vbs znovu používá `GetObject` funkce k vytvoření proxy serveru pro službu.  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Zadejte parametry používané zástupný název:  
  
-   Adresa koncového bodu služby metadata exchange.  
  
-   Adresa koncového bodu služby.  
  
-   Vazby, který klient musí použít pro připojení pomocí tohoto koncového bodu a obor názvů, ve kterém je definován, že vazba. V takovém případě `wsHttpBinding_ICalculator` se používá.  
  
-   Název a obor názvů kontraktu. Tato identifikace totiž jazyka WSDL může obsahovat více než jeden kontrakt.  
  
 Instance proxy s monikeru služby s vytvořen, klientská aplikace může volat metody na proxy serveru, což vede k infrastruktuře moniker služby volání odpovídající operace služby.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Při spuštění ukázky v reakci na operaci se zobrazí v okně Windows Script Host zprávy. Tento příklad ukazuje klient modelu COM, volání COM použití monikeru s kontraktem MEX komunikovat se službou WCF.  
  
#### <a name="to-set-up-and-build-the-sample"></a>K nastavení a sestavit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Z příkazový řádek vývojáře pro sadu Visual Studio, otevřete složku \client\bin, v rámci složky specifické pro jazyk.  
  
    > [!NOTE]
    >  Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 nebo Windows Server 2008 R2, ujistěte se, že spustit příkazový řádek s oprávněními správce.  
  
4.  Zadejte `tlbexp.exe client.dll /out:CalcProxy.tlb` Export knihovny dll do souboru tlb. "Zadejte upozornění exportéru knihovny typů" očekává se, ale není problém, protože obecného typu se nevyžaduje.  
  
5.  Zadejte `regasm.exe /tlb:CalcProxy.tlb client.dll` k registraci typů modelu COM. "Zadejte upozornění exportéru knihovny typů" očekává se, ale není problém, protože obecného typu se nevyžaduje.  
  
6.  Zadejte `gacutil.exe /i client.dll` přidat sestavení do globální mezipaměti sestavení.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Test, který můžete přístup ke službě pomocí prohlížeče tak, že zadáte tuto adresu: `http://localhost/servicemodelsamples/service.svc`. Stránka s potvrzením má být zobrazena v odpovědi.  
  
2.  Spusťte ComCalcClient.vbs z \client ze složky specifické pro jazyk. Činnost klienta se zobrazí v poli zpráv – windows.  
  
3.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích  
  
1.  Na počítači se službou vytvořte virtuální adresář s názvem ServiceModelSamples. Setupvroot.bat skript dodaný s ukázkou je možné vytvořit na disku a virtuální adresář.  
  
2.  Zkopírujte soubory programu služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do ServiceModelSamples virtuálního adresáře na počítači se službou. Nezapomeňte zahrnout soubory v adresáři \bin.  
  
3.  Zkopírujte instalační soubor klienta skriptu ze složky \client v rámci složky specifické pro jazyk do klientského počítače.  
  
4.  V souboru skriptu změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adresu služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.  
  
5.  Zkopírujte soubor WSDL na klientském počítači. V souboru WSDL serviceWsdl.xml, nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.  
  
6.  Zkopírujte Client.dll knihovny ze složky \client\bin v rámci složky specifické pro jazyk do adresáře na klientském počítači.  
  
7.  Z příkazového řádku přejděte do této cílové složky v klientském počítači. Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], ujistěte se, že příkazový řádek spustit jako správce.  
  
8.  Zadejte `tlbexp.exe client.dll /out:CalcProxy.tlb` Export knihovny dll do souboru tlb. "Zadejte upozornění exportéru knihovny typů" očekává se, ale není problém, protože obecného typu se nevyžaduje.  
  
9. Zadejte `regasm.exe /tlb:CalcProxy.tlb client.dll` k registraci typů modelu COM. Zajištění byla nastavena tato cesta ke složce, která obsahuje `regasm.exe` před spuštěním příkazu.  
  
10. Zadejte `gacutil.exe /i client.dll` přidat sestavení do globální mezipaměti sestavení. Zajištění byla nastavena tato cesta ke složce, která obsahuje `gacutil.exe` před spuštěním příkazu.  
  
11. Testovací službě můžete dostat z klientského počítače pomocí prohlížeče.  
  
12. Na klientském počítači spusťte ComCalcClient.vbs.  
  
#### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
-   Z bezpečnostních důvodů odstranit definici virtuální adresář a oprávnění udělené v kroků instalace, až budete hotovi s ukázkami.  
