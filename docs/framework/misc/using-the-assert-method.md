---
title: Použití metody Assert
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
ms.openlocfilehash: 92e49af78d42f360d5798a72d4e7b981295947e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181108"
---
# <a name="using-the-assert-method"></a>Použití metody Assert
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>je metoda, která může být volána na <xref:System.Security.PermissionSet> třídy oprávnění přístupu kódu a na třídu. Assert můžete **použít** k povolení kódu (a příjem volajících) k provádění akcí, které váš kód má oprávnění k provedení, ale jeho volající nemusí mít oprávnění k tomu. Kontrolní výraz zabezpečení změní normální proces, který za běhu provádí během kontroly zabezpečení. Když uplatníte oprávnění, řekne systému zabezpečení, aby nekontroloval volající vašeho kódu pro uplatněné oprávnění.  
  
> [!CAUTION]
> Kontrolní výrazy používejte opatrně, protože mohou otevřít bezpečnostní díry a ohrozit mechanismus běhu runtime pro vynucení bezpečnostních omezení.  
  
 Kontrolní výrazy jsou užitečné v situacích, ve kterých knihovna volá do nespravovaného kódu nebo volání, které vyžaduje oprávnění, které zjevně nesouvisí s zamýšlené použití knihovny. Například všechny spravované kódy, které volají do nespravovaného kódu, musí mít **oprávnění Zabezpečení s** určeným příznakem **UnmanagedCode.** Kód, který nepochází z místního počítače, jako je například kód stažený z místní sítě intranet, nebude ve výchozím nastavení uděleno toto oprávnění. Proto aby kód, který je stažen z místnísítě intranet, aby bylo možné volat knihovnu, která používá nespravovaný kód, musí mít oprávnění uplatněné knihovnou. Některé knihovny mohou navíc volat volajícím, které nejsou viditelné a vyžadují zvláštní oprávnění.  
  
 Kontrolní výrazy můžete také použít v situacích, ve kterých váš kód přistupuje k prostředku způsobem, který je zcela skrytý před volajícími. Předpokládejme například, že knihovna získává informace z databáze, ale v procesu také čte informace z registru počítače. Vzhledem k tomu, že vývojáři, kteří používají vaši knihovnu, nemají přístup k vašemu zdroji, nemají žádný způsob, jak zjistit, že jejich kód vyžaduje **Oprávnění registru,** aby mohli používat váš kód. V takovém případě, pokud se rozhodnete, že není rozumné nebo nutné vyžadovat, aby volající kódu měli oprávnění k přístupu do registru, můžete uplatnit oprávnění ke čtení registru. V takovém případě je vhodné pro knihovnu uplatnit oprávnění tak, aby volající bez **RegistryPermission** můžete použít knihovnu.  
  
 Kontrolní výraz ovlivňuje procházení zásobníku pouze v případě, že uplatněné oprávnění a oprávnění požadované volajícím navazujícím vysíláním jsou stejného typu a pokud je požadované oprávnění podmnožinou uplatněného oprávnění. Pokud například uplatníte **oprávnění FileIOPermission** ke čtení všech souborů na jednotce C a pro FileIOPermission je požadováno, aby **fileiOPermission** četl soubory v C:\Temp, kontrolní výraz může ovlivnit procházení zásobníku; pokud však požadavek byl pro **FileIOPermission** zapisovat na jednotku C, kontrolní výraz by mít žádný vliv.  
  
 Chcete-li provést kontrolní výrazy, musí být vašemu <xref:System.Security.Permissions.SecurityPermission> kódu uděleno oprávnění, které uplatňujete, a to, které představuje právo provádět kontrolní výrazy. I když můžete uplatnit oprávnění, že váš kód nebyl udělen, kontrolní výraz by bylo zbytečné, protože kontrola zabezpečení by se nezdaří dříve, než kontrolní výraz může způsobit jeho úspěšné.  
  
 Následující obrázek znázorňuje, co se stane při použití **assert**. Předpokládejme, že následující příkazy jsou pravdivé o sestaveních A, B, C, E a F a dvou oprávnění, P1 a P1A:  
  
- P1A představuje právo číst soubory TXT na jednotce C.  
  
- P1 představuje právo číst všechny soubory na jednotce C.  
  
- P1A a P1 jsou oba **typy FileIOPermission** a P1A je podmnožinou P1.  
  
- Sestavením E a F bylo uděleno oprávnění P1A.  
  
- Sestavení C bylo uděleno oprávnění P1.  
  
- Sestavení A a B nebyla udělena oprávnění P1 ani P1A.  
  
- Metoda A je obsažena v sestavě A, metoda B je obsažena v sestavě B a tak dále.  
  
 ![Diagram, který znázorňuje sestavení metody Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 V tomto scénáři metoda A volá B, B volá C, C volání E a E volání F. Metoda C uplatňuje oprávnění ke čtení souborů na jednotce C (oprávnění P1) a metoda E vyžaduje oprávnění ke čtení souborů TXT na jednotce C (oprávnění P1A). Při požadavku v F je zjištěna v době běhu, procházení zásobníku se provádí ke kontrole oprávnění všech volajících F, počínaje E. E bylo uděleno oprávnění P1A, takže procházení zásobníku pokračuje zkoumat oprávnění C, kde je zjištěn kontrolní výraz C. Vzhledem k tomu, že požadované oprávnění (P1A) je podmnožinou uplatňovaného oprávnění (P1), procházení zásobníku se zastaví a kontrola zabezpečení se automaticky ustřídá. Nezáleží na tom, že sestavení A a B nebyla udělena oprávnění P1A. Uplatněním P1, metoda C zajišťuje, že jeho volající přístup k prostředku chráněnép1, i v případě, že volající mnebyla udělena oprávnění k přístupu k tomuto prostředku.  
  
 Pokud navrhujete knihovnu tříd a třída přistupuje k chráněnému prostředku, měli byste ve většině případů vytvořit požadavek zabezpečení vyžadující, aby volající třídy měli příslušná oprávnění. Pokud třída pak provede operaci, pro kterou víte, že většina jeho volajících nebude mít oprávnění, a pokud jste ochotni převzít odpovědnost za to, že tito volající volají váš kód, můžete uplatnit oprávnění voláním metody **Assert** na objektu oprávnění, který představuje operaci, kterou kód provádí. Použití **Assert** tímto způsobem umožňuje volajícím, které obvykle nemůže tak učinit volání kódu. Pokud tedy uplatňujete oprávnění, měli byste předem provést příslušné kontroly zabezpečení, abyste zabránili zneužití součásti.  
  
 Předpokládejme například, že vaše vysoce důvěryhodná třída knihovny má metodu, která odstraňuje soubory. Přistupuje k souboru voláním nespravované funkce Win32. Volající vyvolá metodu **Delete** vašeho kódu a předá název souboru, který má být odstraněn, C:\Test.txt. V rámci **Delete** metoda vytvoří <xref:System.Security.Permissions.FileIOPermission> objekt představující přístup pro zápis do C:\Test.txt. (K odstranění souboru je nutný přístup pro zápis.) Váš kód pak vyvolá imperativní kontrolu zabezpečení voláním metody **Demand** objektu **FileIOPermission.** Pokud jeden z volajících v zásobníku volání nemá <xref:System.Security.SecurityException> toto oprávnění, je vyvolána. Pokud není vyvolána žádná výjimka, víte, že všichni volající mají právo na přístup k c:\Test.txt. Vzhledem k tomu, že se domníváte, že většina volajících <xref:System.Security.Permissions.SecurityPermission> nebude mít oprávnění k přístupu k nespravovanému kódu, váš kód pak vytvoří objekt, který představuje právo volat nespravovaný kód a volá metodu **Assert** objektu. Nakonec volá nespravovanou funkci Win32 k odstranění c:\Text.txt a vrátí ovládací prvek volajícímu.  
  
> [!CAUTION]
> Musíte si být jisti, že váš kód nepoužívá kontrolní výrazy v situacích, kdy váš kód může být použit jiným kódem pro přístup k prostředku, který je chráněn oprávněním, které uplatňujete. Například v kódu, který zapisuje do souboru, jehož jméno je určeno volajícím jako parametr, byste neuplatnili **FileIOPermission** pro zápis do souborů, protože váš kód by byl otevřen zneužití třetí stranou.  
  
 Při použití imperativní syntaxe zabezpečení volání **Assert** metoda na více oprávnění ve stejné metodě způsobí, že výjimku zabezpečení, které mají být vyvolány. Místo toho byste měli vytvořit Objekt **PermissionSet,** předat mu jednotlivá oprávnění, která chcete vyvolat, a pak volat metodu **Assert** na objektu **PermissionSet.** Při použití deklarativní syntaxe zabezpečení můžete volat metodu **Assert** více než jednou.  
  
 Následující příklad ukazuje deklarativní syntaxi pro přepsání kontrol zabezpečení pomocí metody **Assert.** Všimněte si, že syntaxe **FileIOPermissionAttribute** má dvě hodnoty: <xref:System.Security.Permissions.SecurityAction> výčet a umístění souboru nebo adresáře, ke kterému má být uděleno oprávnění. Volání **Assert** způsobí, že `C:\Log.txt` požadavky na přístup k úspěšné, i když volající nejsou kontrolovány oprávnění pro přístup k souboru.  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {
      }
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}
```  
  
 Následující fragmenty kódu zobrazují imperativní syntaxi pro přepsání kontrol zabezpečení pomocí metody **Assert.** V tomto příkladu je deklarována instance objektu **FileIOPermission.** Jeho konstruktor je předán **FileIOPermissionAccess.AllAccess** definovat typ přístupu povoleno, následuje řetězec popisující umístění souboru. Jakmile je objekt **FileIOPermission** definován, stačí pouze volat **jeho** assert metodu přepsat kontrolu zabezpečení.  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {
      }
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [Atributy](../../standard/attributes/index.md)
- [Zabezpečení přístupu kódu](code-access-security.md)
