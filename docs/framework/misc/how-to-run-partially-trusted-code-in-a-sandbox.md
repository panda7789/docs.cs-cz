---
title: 'Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru'
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: 0191846f5589b0162ba342161fb5919ff20099d4
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215858"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Sandboxing je postup spuštění kódu v prostředí s omezeným zabezpečením, které omezuje oprávnění k přístupu udělené kódu. Pokud máte například spravovanou knihovnu ze zdroje, kterému nedůvěřujete, neměli byste ji spouštět jako plně důvěryhodnou. Místo toho byste měli umístit kód do izolovaného prostoru (sandbox), který omezí jeho oprávnění na ty, které očekáváte, že bude potřebovat (například <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění).  
  
 K testování kódu, který se bude spouštět v částečně důvěryhodných prostředích, můžete použít také sandboxing.  
  
 <xref:System.AppDomain> je efektivní způsob poskytování izolovaného prostoru pro spravované aplikace. Aplikační domény používané pro spouštění částečně důvěryhodného kódu mají oprávnění definující chráněné prostředky, které jsou k dispozici při spuštění v rámci této <xref:System.AppDomain>. Kód, který běží uvnitř <xref:System.AppDomain>, je vázán oprávněními přidruženými k <xref:System.AppDomain> a má povolen přístup pouze k určeným prostředkům. <xref:System.AppDomain> také obsahuje <xref:System.Security.Policy.StrongName> pole, které se používá k identifikaci sestavení, která mají být načtena jako plně důvěryhodná. To umožňuje autorovi <xref:System.AppDomain> spustit novou doménu v izolovaném prostoru, která umožňuje plně důvěřovat konkrétním podpůrným sestavením. Další možností pro načítání sestavení jako plně důvěryhodných je umístit je do globální mezipaměti sestavení (GAC). to však načte sestavení jako plně důvěryhodných ve všech doménách aplikace vytvořených v daném počítači. Seznam silných názvů podporuje rozhodnutí podle<xref:System.AppDomain>, která poskytují přísnější určení.  
  
 Přetížení metody <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> lze použít k určení sady oprávnění pro aplikace, které jsou spuštěny v izolovaném prostoru (sandboxu). Toto přetížení umožňuje určit přesnou úroveň zabezpečení přístupu kódu, kterou chcete. Sestavení, která jsou načtena do <xref:System.AppDomain> pomocí tohoto přetížení, mohou mít buď zadanou sadu udělení oprávnění, nebo mohou být plně důvěryhodná. Sestavení má úplný vztah důvěryhodnosti, pokud se nachází v globální mezipaměti sestavení (GAC) nebo jsou uvedeny v parametru pole `fullTrustAssemblies` (<xref:System.Security.Policy.StrongName>). Do seznamu `fullTrustAssemblies` by měla být přidána pouze sestavení známá jako plně důvěryhodná.  
  
 Přetížení má následující signaturu:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Parametry pro přetížení metody <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> určují název <xref:System.AppDomain>, legitimace <xref:System.AppDomain>, objekt <xref:System.AppDomainSetup>, který identifikuje základ aplikace pro izolovaný prostor (sandbox), nastavení oprávnění k použití a silné názvy pro plně důvěryhodná sestavení.  
  
 Z bezpečnostních důvodů by základ aplikace zadaný v parametru `info` neměl být základem aplikace pro hostitelskou aplikaci.  
  
 Pro parametr `grantSet` můžete zadat buď sadu oprávnění, kterou jste explicitně vytvořili, nebo standardní sadu oprávnění vytvořenou metodou <xref:System.Security.SecurityManager.GetStandardSandbox%2A>.  
  
 Na rozdíl od většiny <xref:System.AppDomain> načítání se nepoužívá legitimace pro <xref:System.AppDomain> (která je poskytnuta parametrem `securityInfo`) k určení sady udělení pro částečně důvěryhodná sestavení. Místo toho je nezávisle určena parametrem `grantSet`. Legitimace se ale dá použít k jiným účelům, jako je určení oboru izolovaného úložiště.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Spuštění aplikace v izolovaném prostoru  
  
1. Vytvořte sadu oprávnění, která se udělí nedůvěryhodné aplikaci. Minimální oprávnění, které můžete udělit, je <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění. Můžete také udělit další oprávnění, která považujete za bezpečné pro nedůvěryhodný kód. například <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Následující kód vytvoří novou sadu oprávnění pouze s oprávněním <xref:System.Security.Permissions.SecurityPermissionFlag.Execution>.  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Alternativně můžete použít existující pojmenovanou sadu oprávnění, jako je například Internet.  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     Metoda <xref:System.Security.SecurityManager.GetStandardSandbox%2A> vrací buď sadu oprávnění `Internet`, nebo `LocalIntranet` sadu oprávnění v závislosti na zóně v legitimaci. <xref:System.Security.SecurityManager.GetStandardSandbox%2A> také vytvoří oprávnění identity pro některé objekty legitimace předané jako odkazy.  
  
2. Podepište sestavení, které obsahuje třídu hostování (s názvem `Sandboxer` v tomto příkladu), která volá nedůvěryhodný kód. Přidejte <xref:System.Security.Policy.StrongName>, který se používá k podepsání sestavení, do pole <xref:System.Security.Policy.StrongName> parametru `fullTrustAssemblies` <xref:System.AppDomain.CreateDomain%2A> volání. Třída hosting musí běžet jako plně důvěryhodná, aby bylo možné spustit kód s částečným vztahem důvěryhodnosti nebo nabízet služby pro aplikaci s částečným vztahem důvěryhodnosti. Tímto způsobem si přečtete <xref:System.Security.Policy.StrongName> sestavení:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     .NET Framework sestavení, jako například mscorlib a System. dll, není nutné přidávat do seznamu úplných vztahů důvěryhodnosti, protože jsou načteny jako plně důvěryhodné z globální mezipaměti sestavení (GAC).  
  
3. Inicializujte parametr <xref:System.AppDomainSetup> metody <xref:System.AppDomain.CreateDomain%2A>. Pomocí tohoto parametru můžete ovládat mnoho nastavení nového <xref:System.AppDomain>. Vlastnost <xref:System.AppDomainSetup.ApplicationBase%2A> je důležité nastavení a měla by se lišit od vlastnosti <xref:System.AppDomainSetup.ApplicationBase%2A> pro <xref:System.AppDomain> hostující aplikace. Pokud jsou nastavení <xref:System.AppDomainSetup.ApplicationBase%2A> shodná, může aplikace s částečnou důvěryhodností načíst hostitelskou aplikaci (jako plně důvěryhodnou) výjimku, kterou definuje, a zneužije ji tak. Toto je další důvod, proč se nedoporučuje zachytit (výjimka). Nastavení základu aplikace hostitele odlišně od základu aplikace v izolovaném prostoru (sandbox) snižuje riziko zneužití.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. Zavolejte přetížení metody <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> k vytvoření domény aplikace pomocí zadaných parametrů.  
  
     Signatura této metody je:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Další informace:  
  
    - Toto je jediné přetížení metody <xref:System.AppDomain.CreateDomain%2A>, které přebírá <xref:System.Security.PermissionSet> jako parametr, a tak jediné přetížení, které umožňuje načíst aplikaci v nastavení částečné důvěryhodnosti.  
  
    - Parametr `evidence` se nepoužívá k výpočtu sady oprávnění; používá se pro identifikaci jinými funkcemi .NET Framework.  
  
    - Nastavení vlastnosti <xref:System.AppDomainSetup.ApplicationBase%2A> parametru `info` je pro toto přetížení povinné.  
  
    - Parametr `fullTrustAssemblies` obsahuje klíčové slovo `params`, což znamená, že není nutné vytvářet pole <xref:System.Security.Policy.StrongName>. Předání 0, 1 nebo více silných názvů jako parametrů je povoleno.  
  
    - Kód pro vytvoření aplikační domény je:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. Načtěte kód do sandboxing <xref:System.AppDomain>, který jste vytvořili. To lze provést dvěma způsoby:  
  
    - Pro sestavení volejte metodu <xref:System.AppDomain.ExecuteAssembly%2A>.  
  
    - Použijte metodu <xref:System.Activator.CreateInstanceFrom%2A> k vytvoření instance třídy odvozené z <xref:System.MarshalByRefObject> v novém <xref:System.AppDomain>.  
  
     Druhý způsob je vhodnější, protože usnadňuje předávání parametrů nové instanci <xref:System.AppDomain>. Metoda <xref:System.Activator.CreateInstanceFrom%2A> poskytuje dvě důležité funkce:  
  
    - Můžete použít základ kódu, který odkazuje na umístění, které neobsahuje vaše sestavení.  
  
    - Vytvoření můžete provést v rámci <xref:System.Security.CodeAccessPermission.Assert%2A> pro plně důvěryhodné (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), což umožňuje vytvořit instanci kritické třídy. (K tomu dojde vždy, když vaše sestavení nemá žádné značky transparentnosti a je načteno jako plně důvěryhodné.) Proto je třeba pečlivě vytvořit pouze kód, kterému důvěřujete pomocí této funkce, a doporučujeme vytvořit pouze instance plně důvěryhodných tříd v nové doméně aplikace.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Všimněte si, že aby bylo možné vytvořit instanci třídy v nové doméně, musí třída rozšiřuje třídu <xref:System.MarshalByRefObject>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. Rozbalení nové instance domény do odkazu v této doméně. Tento odkaz slouží ke spuštění nedůvěryhodného kódu.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. Volejte metodu `ExecuteUntrustedCode` v instanci `Sandboxer` třídy, kterou jste právě vytvořili.  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     Toto volání je spuštěno v doméně aplikace v izolovaném prostoru, která má omezená oprávnění.  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is   
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <xref:System.Reflection> slouží k získání popisovače metody v částečně důvěryhodném sestavení. Popisovač lze použít ke spuštění kódu bezpečným způsobem s minimálními oprávněními.  
  
     V předchozím kódu si poznamenejte <xref:System.Security.PermissionSet.Assert%2A> pro oprávnění plné důvěryhodnosti před tiskem <xref:System.Security.SecurityException>.  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     Výraz s úplným vztahem důvěryhodnosti se používá k získání rozšířených informací z <xref:System.Security.SecurityException>. Bez <xref:System.Security.PermissionSet.Assert%2A><xref:System.Security.SecurityException.ToString%2A> metoda <xref:System.Security.SecurityException> zjistí, že v zásobníku je částečně důvěryhodný kód a omezí vrácené informace. To může způsobit problémy se zabezpečením, pokud by kód částečného vztahu důvěryhodnosti mohl tyto informace přečíst, ale riziko je zmírnit tím, že neudělí <xref:System.Security.Permissions.UIPermission>. Kontrolní výraz s úplným vztahem důvěryhodnosti by měl být použit zřídka a pouze v případě, že jste si jisti, že nepovolujete použití kódu s částečným vztahem důvěryhodnosti ke zvýšení na úplný vztah důvěryhodnosti. Jako pravidlo Nevolejte kód, který nedůvěřujete ve stejné funkci a poté, co jste volali kontrolní výraz pro úplný vztah důvěryhodnosti. Je dobrým zvykem, abyste po dokončení používání kontrolního výrazu vždy vrátili.  
  
## <a name="example"></a>Příklad  
 Následující příklad implementuje postup v předchozí části. V příkladu projekt s názvem `Sandboxer` v řešení sady Visual Studio obsahuje také projekt s názvem `UntrustedCode`, který implementuje `UntrustedClass`třídy. V tomto scénáři se předpokládá, že jste stáhli sestavení knihovny obsahující metodu, která má vrátit `true` nebo `false` k označení, zda je zadané číslo Fibonacci číslem. Místo toho se metoda pokusí přečíst soubor z počítače. Následující příklad ukazuje nedůvěryhodný kód.  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 Následující příklad ukazuje `Sandboxer` kód aplikace, který spouští nedůvěryhodný kód.  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another   
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder   
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to   
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.   
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the   
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are   
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
