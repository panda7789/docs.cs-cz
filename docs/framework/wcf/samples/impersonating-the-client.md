---
title: Zosobnění klienta
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 5a13ab73e48616b38e583b1c9948fc1bf5eb8a64
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43522285"
---
# <a name="impersonating-the-client"></a>Zosobnění klienta
Ukázka zosobnění ukazuje, jak zosobnit volající aplikace na službu tak, aby službě můžete získat přístup k systémovým prostředkům jménem volající.  
  
 Tato ukázka je založena na [hostování na vlastním serveru](../../../../docs/framework/wcf/samples/self-host.md) vzorku. Konfigurační soubory klienta a služby jsou stejné jako u [hostování na vlastním serveru](../../../../docs/framework/wcf/samples/self-host.md) vzorku.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Kód služby byla změněna tak, aby `Add` zosobňuje volající pomocí metody ve službě <xref:System.ServiceModel.OperationBehaviorAttribute> jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    Console.WriteLine("Received Add({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 V důsledku toho přepnutí kontextu zabezpečení spuštěné vlákno na zosobňují volajícího před vstupem `Add` metoda a vrátit zpět k ukončení metodu.  
  
 `DisplayIdentityInformation` Metoda je znázorněno v následujícím ukázkovém kódu je nástroj pro funkci, která zobrazuje identitu volajícího.  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tThread Identity            :{0}",  
         WindowsIdentity.GetCurrent().Name);  
    Console.WriteLine("\t\tThread Identity level  :{0}",   
         WindowsIdentity.GetCurrent().ImpersonationLevel);  
    Console.WriteLine("\t\thToken                     :{0}",  
         WindowsIdentity.GetCurrent().Token.ToString());  
    return;  
}  
```  
  
 `Subtract` Metoda ve službě zosobňuje volající pomocí imperativního volání, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
public double Subtract(double n1, double n2)  
{  
    double result = n1 - n2;  
    Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
Console.WriteLine("Before impersonating");  
DisplayIdentityInformation();  
  
    if (ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Impersonation ||  
        ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Delegation)  
    {  
        // Impersonate.  
        using (ServiceSecurityContext.Current.WindowsIdentity.Impersonate())  
        {  
            // Make a system call in the caller's context and ACLs   
            // on the system resource are enforced in the caller's context.   
            Console.WriteLine("Impersonating the caller imperatively");  
            DisplayIdentityInformation();  
        }  
    }  
    else  
    {  
        Console.WriteLine("ImpersonationLevel is not high enough to perform this operation.");  
    }  
  
Console.WriteLine("After reverting");  
DisplayIdentityInformation();  
    return result;  
}  
```  
  
 Všimněte si, že v tomto případě volající není zosobnit celý volání, ale je jen zosobněné část volání. Zosobnění pro nejmenší obor je obecně vhodnější zosobnění pro celou operaci.  
  
 Jiné metody není zosobňují volajícího.  
  
 Klientský kód byl změněn na nastavení úrovně k zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>. Určuje úroveň zosobnění použije službu, pomocí klienta <xref:System.Security.Principal.TokenImpersonationLevel> výčtu. Výčet podporuje následující hodnoty: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> a <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. K provedení kontroly přístupu při přístupu k systémového prostředku v místním počítači, který je chráněn pomocí ACL Windows, musí být nastavena úroveň zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazují v oknech konzoly služby a klienta. Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.  
  
> [!NOTE]
>  Služba se musí buď spustit pod účtem správce nebo účet běží pod musí mít udělena oprávnění k registraci http://localhost:8000/ServiceModelSamples identifikátor URI s vrstvou HTTP. Tato oprávnění lze udělit nastavením [Namespace rezervace](https://go.microsoft.com/fwlink/?LinkId=95012) pomocí [Httpcfg.exe nástroj](https://go.microsoft.com/fwlink/?LinkId=95010).  
  
> [!NOTE]
>  V počítačích se systémem [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], zosobnění je podporována pouze v případě, že aplikace Host.exe má oprávnění k zosobnění. (Ve výchozím nastavení, pouze správci mají toto oprávnění.) Pokud chcete přidat toto oprávnění je služba spuštěna jako účet, přejděte na **nástroje pro správu**, otevřete **místní zásady zabezpečení**, otevřete **místní zásady**, klikněte na tlačítko **Přiřazení uživatelských práv**a vyberte **zosobnit klienta po ověření** a dvakrát klikněte na panel **vlastnosti** přidat uživatele nebo skupinu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4.  Abychom si předvedli, že služba zosobňuje volajícího, spustíte klienta pod jiným účtem než ten, který je služba spuštěná pod. Provedete to tak, že na příkazovém řádku zadejte:  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Zobrazí se výzva k zadání hesla. Zadejte heslo pro účet, který jste dříve zadali.  
  
5.  Když spustíte klienta, si povšimněte identity před a po spuštění s jinými přihlašovacími údaji.  
  
## <a name="see-also"></a>Viz také
