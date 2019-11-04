---
title: Použití monikeru služby WCF u klientů modelu COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 321d59285b0ef86e4631634d90229a0d8e79657b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424725"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>Použití monikeru služby WCF u klientů modelu COM
Tato ukázka předvádí, jak použít moniker služby Windows Communication Foundation (WCF) k integraci webových služeb do vývojových prostředí založených na modelu COM, jako je například systém Microsoft Office jazyk Visual Basic for Application (Office VBA) nebo Visual Basic 6,0. Tato ukázka se skládá z klienta Windows Script Host (. vbs), podpůrné klientské knihovny (. dll) a knihovny služeb (. dll) hostované službou Internetová informační služba (IIS). Služba je služba kalkulačky a klient modelu COM volá matematické operace – přidat, odečíst, vynásobit a rozdělit – u služby. Aktivita klienta se zobrazí v okně se zprávou okna.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 Služba implementuje kontrakt `ICalculator`, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Ukázka předvádí tři alternativní přístupy k použití monikeru:  
  
- Typ kontraktu – kontrakt se na klientském počítači zaregistruje jako viditelný typ modelu COM.  
  
- Smlouva WSDL – smlouva je dodávána ve formě dokumentu WSDL.  
  
- Smlouva o výměně metadat – smlouva se načte za běhu z koncového bodu výměny metadat (MEX).  
  
## <a name="typed-contract"></a>Zadaný kontrakt  
 Aby bylo možné použít moniker se zadaným typem kontraktu, musí být odpovídající typy pro kontrakt služby zaregistrované v modelu COM. Nejdřív je potřeba, aby se klient vygeneroval pomocí [Nástroje pro použití metadat ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Spusťte následující příkaz z příkazového řádku v adresáři klienta pro vygenerování typovaného proxy serveru.  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Tato třída musí být zahrnutá v projektu a projekt by měl být nakonfigurovaný tak, aby při kompilaci generoval podepsané sestavení viditelné pomocí modelu COM. Do souboru AssemblyInfo.cs by měl být zahrnut následující atribut.  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 Po sestavení projektu Zaregistrujte typy viditelné modelem COM pomocí `regasm`, jak je znázorněno v následujícím příkladu.  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 Sestavení, které je vytvořeno, by mělo být přidáno do globální mezipaměti sestavení (GAC). I když není nezbytně nutné, zjednodušuje proces, který vyhledává sestavení. Následující příkaz přidá sestavení do globální mezipaměti sestavení (GAC).  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> Moniker služby vyžaduje jenom registraci typu a nepoužívá proxy ke komunikaci se službou.  
  
 Klientská aplikace ComCalcClient. vbs používá funkci `GetObject` k vytvoření proxy serveru pro službu pomocí syntaxe monikeru služby k určení adresy, vazby a kontraktu služby.  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Parametry používané monikerem určují:  
  
- Adresa koncového bodu služby.  
  
- Vazba, kterou by měl klient použít pro připojení k tomuto koncovému bodu. V takovém případě se používá systém wsHttpBinding definovaný i v případě, že vlastní vazby lze definovat v konfiguračních souborech klienta. Pro použití s modulem Windows Script Host je vlastní vazba definovaná v souboru Cscript. exe. config ve stejném adresáři jako Cscript. exe.  
  
- Typ kontraktu, který je podporován na koncovém bodu. Toto je typ, který se vygeneroval a zaregistroval výše. Protože Visual Basic skript neposkytuje prostředí COM silného typu, musí být zadán identifikátor pro kontrakt. Identifikátor GUID je `interfaceID` z CalcProxy. tlb, kterou lze zobrazit pomocí nástrojů modelu COM, jako je například prohlížeč objektů OLE/COM (OleView. exe). Pro prostředí se silnými typy, jako je například Office VBA nebo Visual Basic 6,0, se do knihovny typů přidá explicitní odkaz a potom se dá deklarovat typ objektu proxy místo parametru kontraktu. Tato funkce také poskytuje podporu technologie IntelliSense během vývoje klientských aplikací.  
  
 Po sestavení instance proxy k monikeru služby může klientská aplikace volat metody na proxy serveru, což vede k tomu, že infrastruktura monikeru služby volá odpovídající operace služby.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Při spuštění ukázky se odpověď na operaci zobrazí v okně se zprávou hostitele Windows Script Host. To ukazuje klientovi modelu COM, který provádí volání COM pomocí typového monikeru ke komunikaci se službou WCF. Bez ohledu na použití modelu COM v klientské aplikaci se komunikace se službou skládá pouze z volání webové služby.  
  
## <a name="wsdl-contract"></a>Kontrakt WSDL  
 Chcete-li použít moniker se smlouvou WSDL, není vyžadována registrace klientské knihovny, ale kontrakt WSDL pro službu musí být načten pomocí mechanismu mimo IP síť, jako je například použití prohlížeče pro přístup ke koncovému bodu WSDL pro danou službu. Moniker pak může k této smlouvě přistupovat v době spuštění.  
  
 Klientská aplikace ComCalcClient. vbs používá `FileSystemObject` k přístupu k místně uloženému souboru WSDL a potom znovu používá funkci `GetObject` k vytvoření proxy pro službu.  
  
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
  
 Parametry používané monikerem určují:  
  
- Adresa koncového bodu služby.  
  
- Vazba, kterou by měl klient použít pro připojení k tomuto koncovému bodu, a obor názvů, ve kterém je tato vazba definovaná. V tomto případě se používá `wsHttpBinding_ICalculator`.  
  
- WSDL, který definuje kontrakt. V tomto případě se jedná o řetězec, který byl načten ze souboru serviceWsdl. XML.  
  
- Název a obor názvů kontraktu. Tato identifikace je povinná, protože WSDL může obsahovat více než jeden kontrakt.  
  
    > [!NOTE]
    > Ve výchozím nastavení generují služby WCF samostatné soubory WSDL pro každý obor názvů, který používá. Tyto prvky jsou propojeny s použitím importované konstrukce WSDL. Vzhledem k tomu, že moniker očekává jednu definici WSDL, služba musí buď použít jeden obor názvů, jak je znázorněno v této ukázce, nebo samostatné soubory musí být ručně sloučeny.  
  
 Po sestavení instance proxy k monikeru služby může klientská aplikace volat metody na proxy serveru, což vede k tomu, že infrastruktura monikeru služby volá odpovídající operace služby.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Při spuštění ukázky se odpověď na operaci zobrazí v okně se zprávou hostitele Windows Script Host. To ukazuje klientovi modelu COM, který provádí volání COM pomocí monikeru s kontraktem WSDL ke komunikaci se službou WCF.  
  
## <a name="metadata-exchange-contract"></a>Kontrakt pro výměnu metadat  
 Chcete-li použít moniker se smlouvou MEX, stejně jako u kontraktu WSDL, není vyžadována registrace klienta. Smlouva pro službu je načtena v době provádění prostřednictvím interního použití výměny metadat.  
  
 Klientská aplikace ComCalcClient. vbs znovu používá funkci `GetObject` k vytvoření proxy serveru pro danou službu.  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Parametry používané monikerem určují:  
  
- Adresa koncového bodu výměny metadat služby.  
  
- Adresa koncového bodu služby.  
  
- Vazba, kterou by měl klient použít pro připojení k tomuto koncovému bodu, a obor názvů, ve kterém je tato vazba definovaná. V tomto případě se používá `wsHttpBinding_ICalculator`.  
  
- Název a obor názvů kontraktu. Tato identifikace je povinná, protože WSDL může obsahovat více než jeden kontrakt.  
  
 Po sestavení instance proxy k monikeru služby může klientská aplikace volat metody na proxy serveru, což vede k tomu, že infrastruktura monikeru služby volá odpovídající operace služby.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Při spuštění ukázky se odpověď na operaci zobrazí v okně se zprávou hostitele Windows Script Host. To ukazuje klientovi modelu COM, který provádí volání COM pomocí monikeru se smlouvou MEX ke komunikaci se službou WCF.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Z Developer Command Prompt pro Visual Studio otevřete složku \client\bin ve složce specifické pro jazyk.  
  
    > [!NOTE]
    > Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 nebo Windows Server 2008 R2, ujistěte se, že jste spustili příkazový řádek s oprávněními správce.  
  
4. Zadejte `tlbexp.exe client.dll /out:CalcProxy.tlb` pro export knihovny DLL do souboru TLB. Očekává se "upozornění exportéra knihovny typů", ale nejedná se o problém, protože obecný typ není povinný.  
  
5. Zadejte `regasm.exe /tlb:CalcProxy.tlb client.dll` pro registraci typů pomocí modelu COM. Očekává se "upozornění exportéra knihovny typů", ale nejedná se o problém, protože obecný typ není povinný.  
  
6. Zadejte `gacutil.exe /i client.dll`, chcete-li přidat sestavení do globální mezipaměti sestavení (GAC).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači  
  
1. Otestujte, zda ke službě můžete přistupovat pomocí prohlížeče zadáním následující adresy: `http://localhost/servicemodelsamples/service.svc`. V odpovědi by se měla zobrazit Stránka s potvrzením.  
  
2. Spusťte ComCalcClient. vbs z \Client, ze složky pro konkrétní jazyk. Aktivita klienta se zobrazí v oknech se zprávou.  
  
3. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači  
  
1. Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples. Skript Setupvroot. bat, který je součástí ukázky, se dá použít k vytvoření adresáře disku a virtuálního adresáře.  
  
2. Zkopírujte programové soubory služby z%SystemDrive%\Inetpub\wwwroot\servicemodelsamples do virtuálního adresáře ServiceModelSamples na počítači služby. Nezapomeňte zahrnout soubory do adresáře \Bin.  
  
3. Zkopírujte soubor skriptu klienta ze složky \Client ve složce pro konkrétní jazyk do klientského počítače.  
  
4. V souboru skriptu změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese vaší služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.  
  
5. Zkopírujte soubor WSDL do klientského počítače. V souboru WSDL serviceWsdl. XML nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.  
  
6. Zkopírujte knihovnu Client. dll ze složky \client\bin ve složce pro konkrétní jazyk do adresáře v klientském počítači.  
  
7. Z příkazového řádku přejděte do cílového adresáře v klientském počítači. Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], ujistěte se, že se příkazový řádek spouští jako správce.  
  
8. Zadejte `tlbexp.exe client.dll /out:CalcProxy.tlb` pro export knihovny DLL do souboru TLB. Očekává se "upozornění exportéra knihovny typů", ale nejedná se o problém, protože obecný typ není povinný.  
  
9. Zadejte `regasm.exe /tlb:CalcProxy.tlb client.dll` pro registraci typů pomocí modelu COM. Před spuštěním příkazu zajistěte, aby byla cesta nastavená na složku, která obsahuje `regasm.exe`.  
  
10. Zadejte `gacutil.exe /i client.dll`, chcete-li přidat sestavení do globální mezipaměti sestavení (GAC). Před spuštěním příkazu zajistěte, aby byla cesta nastavená na složku, která obsahuje `gacutil.exe`.  
  
11. Otestujte, zda ke službě můžete přistupovat z klientského počítače pomocí prohlížeče.  
  
12. V klientském počítači spusťte ComCalcClient. vbs.  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
- Z bezpečnostních důvodů odeberte definici virtuálního adresáře a oprávnění udělená v krocích instalace, až budete hotovi s ukázkami.  
