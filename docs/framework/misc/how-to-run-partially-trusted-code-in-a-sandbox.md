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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5728bac27ae7de649806a3e026bb16560fffefa
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613216"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a>Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Izolace (sandbox) je spouštění kódu v prostředí s omezeným přístupem, který omezuje oprávnění udělená kódu. Například pokud máte spravované knihovny ze zdroje, kterému nedůvěřujete úplně, byste neměli spouštět ji jako plně důvěryhodné. Místo toho by měl umístit kódu v izolovaném prostoru, který omezuje oprávnění pro ty, které očekáváte, že bude potřebovat (například <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění).  
  
 Izolace (sandbox) můžete také použít k testování kódu, který budete distribuovat, který se spustí v prostředí částečně důvěryhodných.  
  
 <xref:System.AppDomain> Nabízí efektivní způsob poskytování sandboxu pro spravované aplikace. Aplikační domény, které se používají pro spuštění částečně důvěryhodného kódu mají oprávnění, které definují chráněné prostředky, které jsou k dispozici při spuštění v rámci, která <xref:System.AppDomain>. Kód, který běží v rámci <xref:System.AppDomain> oprávnění spojená s vázán <xref:System.AppDomain> a je povolen přístup pouze zadané prostředky. <xref:System.AppDomain> Zahrnuje také <xref:System.Security.Policy.StrongName> pole, které slouží k identifikaci sestavení, které mají být načteno jako plně důvěryhodné. To umožňuje Tvůrce <xref:System.AppDomain> spustit novou doménu v izolovaném prostoru, který umožňuje konkrétní pomocné rutiny sestavení být plně důvěryhodné. Další možností pro načtení sestavení jako plně důvěryhodné je umístit je do globální mezipaměti sestavení; Nicméně, který načte sestavení jako plně důvěryhodný ve všech doménách aplikace vytvořené v tomto počítači. Seznam silných názvů podporuje za-<xref:System.AppDomain> rozhodnutí, která poskytuje více omezující rozhodnutí.  
  
 Můžete použít <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení metody k určení oprávnění nastavena pro aplikace, které běží v izolovaném prostoru. Toto přetížení umožňuje určit přesnou úroveň zabezpečení přístupu kódu, který chcete. Sestavení, která jsou načtena do <xref:System.AppDomain> pomocí tohoto přetížení, mohou mít buď zadaný jenom sada udělení oprávnění, nebo může být plně důvěryhodné. Sestavení je udělena úplná důvěryhodnost, pokud se nachází v globální mezipaměti sestavení nebo uvedené v `fullTrustAssemblies` ( <xref:System.Security.Policy.StrongName>) parametr pole. Pouze sestavení, které jsou známé jako plně důvěryhodné by měl být přidány do `fullTrustAssemblies` seznamu.  
  
 Přetížení má následující podpis:  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 Parametry pro <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody zadejte název <xref:System.AppDomain>, legitimaci <xref:System.AppDomain>, <xref:System.AppDomainSetup> objekt, který identifikuje základní aplikace izolovaného prostoru, oprávnění nastaveno na používání a silných názvů pro plně důvěryhodných sestavení.  
  
 Z bezpečnostních důvodů základ cesty aplikace podle `info` parametr nemůže být pro hostitelskou aplikaci základu cesty aplikace.  
  
 Pro `grantSet` parametr, můžete zadat sadu oprávnění, kterou jste vytvořili explicitně nebo standardní oprávnění vytvořená <xref:System.Security.SecurityManager.GetStandardSandbox%2A> metody.  
  
 Na rozdíl od většiny <xref:System.AppDomain> důkaz pro načtení <xref:System.AppDomain> (které poskytuje `securityInfo` parametr) se používá k určení udělenou sadu pro částečně důvěryhodná sestavení. Místo toho je nezávisle určena podle `grantSet` parametru. Legitimace však lze použít pro jiné účely, jako je například určování rozsahu izolovaného úložiště.  
  
### <a name="to-run-an-application-in-a-sandbox"></a>Ke spuštění aplikace v izolovaném prostoru  
  
1.  Vytvořte sadu nedůvěryhodné aplikaci udělit oprávnění. Je minimální oprávnění může udělit <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění. Můžete také udělit další oprávnění, které si myslíte, že může být bezpečné pro nedůvěryhodný kód; například <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Následující kód vytvoří nová sada oprávnění s pouze <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> oprávnění.  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     Alternativně můžete použít existující sadu pojmenovaných oprávnění, jako je například Internet.  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <xref:System.Security.SecurityManager.GetStandardSandbox%2A> Metoda vrátí buď `Internet` sadu oprávnění nebo `LocalIntranet` sadu v závislosti na zóně legitimace oprávnění. <xref:System.Security.SecurityManager.GetStandardSandbox%2A> také vytvoří identitu oprávnění pro některé objekty důkazy předané jako odkazy.  
  
2.  Podepište sestavení obsahující hostující třídy (s názvem `Sandboxer` v tomto příkladu), která volá nedůvěryhodného kódu. Přidat <xref:System.Security.Policy.StrongName> použitý k podepsání sestavení <xref:System.Security.Policy.StrongName> pole `fullTrustAssemblies` parametr <xref:System.AppDomain.CreateDomain%2A> volání. Hostující třídy musí běžet jako plně důvěryhodné povolit spuštění částečně důvěryhodného kódu nebo chcete nabízet služby do aplikace částečným vztahem důvěryhodnosti. To je, jak číst <xref:System.Security.Policy.StrongName> sestavení:  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     Sestavení rozhraní .NET framework, jako je například mscorlib a System.dll, není potřeba přidat do seznamu úplného vztahu důvěryhodnosti, protože pocházejí z globální mezipaměti sestavení načteno jako plně důvěryhodné.  
  
3.  Inicializovat <xref:System.AppDomainSetup> parametr <xref:System.AppDomain.CreateDomain%2A> metody. S tímto parametrem, můžete řídit celou řadu z nastavení nového <xref:System.AppDomain>. <xref:System.AppDomainSetup.ApplicationBase%2A> Vlastnost je důležitá nastavení a musí být odlišný od <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost <xref:System.AppDomain> hostitelské aplikace. Pokud <xref:System.AppDomainSetup.ApplicationBase%2A> nastavení jsou stejné, částečným vztahem důvěryhodnosti aplikace můžete získat hostitelskou aplikaci k načtení (jako plně důvěryhodné) definuje, tedy zneužít výjimky. To je další důvod, proč se nedoporučuje catch (exception). Nastavení aplikace base hostitele odlišně od základ cesty aplikace z aplikace v izolovaném prostoru snižuje riziko zneužití.  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4.  Volání <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> přetížení metody k vytvoření domény aplikace pomocí parametrů jsme určili.  
  
     Signatura pro tuto metodu je:  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     Další informace:  
  
    -   Toto je pouze přetížení <xref:System.AppDomain.CreateDomain%2A> metodu, která přebírá <xref:System.Security.PermissionSet> jako parametr a tedy pouze přetížení, která umožňuje načtení aplikace v částečným vztahem důvěryhodnosti nastavení.  
  
    -   `evidence` Parametr se používá k výpočtu sadu oprávnění, se používá k identifikaci dalších funkcí rozhraní .NET Framework.  
  
    -   Nastavení <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost `info` parametr je povinný pro toto přetížení.  
  
    -   `fullTrustAssemblies` Parametr má `params` – klíčové slovo, což znamená, že není nutné vytvořit <xref:System.Security.Policy.StrongName> pole. Předejte 0, 1 nebo více silných názvů jako parametry je povolen.  
  
    -   Kód k vytvoření domény aplikace je:  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5.  Načíst kód do sandboxing <xref:System.AppDomain> , kterou jste vytvořili. To lze provést dvěma způsoby:  
  
    -   Volání <xref:System.AppDomain.ExecuteAssembly%2A> metodu pro sestavení.  
  
    -   Použití <xref:System.Activator.CreateInstanceFrom%2A> metodu pro vytvoření instance třídy odvozené z <xref:System.MarshalByRefObject> na novém <xref:System.AppDomain>.  
  
     Druhý způsob je vhodnější, protože usnadňuje pro předání parametrů do nového <xref:System.AppDomain> instance. <xref:System.Activator.CreateInstanceFrom%2A> Metoda obsahuje dvě důležité funkce:  
  
    -   Můžete použít, který odkazuje na umístění, které vaše sestavení neobsahuje základ kódu.  
  
    -   Vám pomůžou vytvářet v rámci <xref:System.Security.CodeAccessPermission.Assert%2A> pro plnou důvěryhodnost (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), což vám umožní vytvořit instanci třídy kritické. (Tento proces probíhá vždy sestavení nemá žádné označení transparentnosti a je načteno jako plně důvěryhodné.) Proto budete muset pečlivě vytvořit pouze kód, kterému důvěřujete s touto funkcí a doporučujeme vytvořit pouze instance plně důvěryhodné tříd v nové doméně aplikace.  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     Všimněte si, že k vytvoření instance třídy v nové doméně, třída má rozšířit <xref:System.MarshalByRefObject> třídy  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6.  Rozbalení novou instanci domény do odkazu v této doméně. Tento odkaz se používá ke spuštění nedůvěryhodného kódu.  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7.  Volání `ExecuteUntrustedCode` metoda v instanci aplikace `Sandboxer` třídy, které jste právě vytvořili.  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     Toto volání je proveden v doméně aplikace v izolovaném prostoru, který má omezená oprávnění.  
  
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
  
     <xref:System.Reflection> slouží k získání popisovače metody v částečně důvěryhodné sestavení. Popisovač lze použít ke spouštění kódu vytvořeného bezpečným způsobem s minimálními oprávněními.  
  
     V předchozím kódu, mějte na paměti <xref:System.Security.PermissionSet.Assert%2A> oprávnění plné důvěryhodnosti před tiskem <xref:System.Security.SecurityException>.  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     Kontrolní výraz úplného vztahu důvěryhodnosti se používá k získání rozšířené informace z <xref:System.Security.SecurityException>. Bez <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> metoda <xref:System.Security.SecurityException> zjistí, že je částečně důvěryhodného kódu v zásobníku a omezí vrácené informace. To může způsobit problémy se zabezpečením, pokud částečně důvěryhodného kódu, které může číst informace, ale riziko zmírnit neudělením <xref:System.Security.Permissions.UIPermission>. Kontrolní výraz úplného vztahu důvěryhodnosti měly používat střídmě, a pouze v případě, že jste si jisti, že nepovoluje částečně důvěryhodného kódu zvýšit oprávnění na úplný vztah důvěryhodnosti. Zpravidla Nevolejte kód, který nedůvěřujete ve stejné funkci a po volání assert pro úplný vztah důvěryhodnosti. Je vhodné po dokončení jeho použití se vždycky vrátit assert.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se implementuje podle postupu v předchozí části. V tomto příkladu projekt s názvem `Sandboxer` řešení v sadě Visual Studio, také obsahuje projekt s názvem `UntrustedCode`, který implementuje třídu `UntrustedClass`. Tento scénář předpokládá, že jste si stáhli sestavení knihovny obsahující metodu, která se očekává navrácení `true` nebo `false` označující, zda číslo jste zadali, je Fibonacciho číslo. Místo toho metodu se pokusí přečíst soubor z vašeho počítače. Následující příklad ukazuje nedůvěryhodný kód.  
  
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
  
 Následující příklad ukazuje `Sandboxer` aplikační kód, který provede nedůvěryhodný kód.  
  
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
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
