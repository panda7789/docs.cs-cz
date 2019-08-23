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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b5a13b362f565cfae9247908bcf3cf35c899ae4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910723"
---
# <a name="using-the-assert-method"></a>Použití metody Assert
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>je metoda, která může být volána u tříd oprávnění přístupu kódu a <xref:System.Security.PermissionSet> třídy. Pomocí **výrazu Assert** můžete povolit váš kód (a volajícím) provádět akce, ke kterým má váš kód oprávnění, ale jeho volající nemusí mít oprávnění k tomu. Kontrolní výraz zabezpečení mění běžný proces, který modul runtime provede během kontroly zabezpečení. Pokud vyhodnotit oprávnění, sdělí systému zabezpečení, aby nekontroloval volající kód pro kontrolní oprávnění.  
  
> [!CAUTION]
>  Používejte kontrolní výrazy pečlivě, protože mohou otevírat bezpečnostní otvory a podrušovat mechanismus modulu runtime pro vynucování omezení zabezpečení.  
  
 Kontrolní výrazy jsou užitečné v situacích, kdy knihovna volá do nespravovaného kódu nebo provádí volání vyžadující oprávnění, které není zjevně související s zamýšleným použitím knihovny. Například všechen spravovaný kód, který volá do nespravovaného kódu, musí mít **SecurityPermission** s určeným příznakem. Kód, který nepochází z místního počítače, jako je například kód stažený z místního intranetu, nebude toto oprávnění ve výchozím nastavení uděleno. Proto aby kód, který je stažen z místního intranetu, mohl volat knihovnu, která používá nespravovaný kód, musí mít oprávnění, které je pro knihovnu uplatněno. Kromě toho mohou některé knihovny vyvolat volání, která jsou nepřesná volajícím a vyžadují zvláštní oprávnění.  
  
 Můžete také použít kontrolní výrazy v situacích, ve kterých váš kód přistupuje k prostředku způsobem, který je zcela skrytý od volajících. Předpokládejme například, že vaše knihovna získává informace z databáze, ale v procesu také čte informace z registru počítače. Vzhledem k tomu, že vývojáři, kteří používají vaši knihovnu, nemají přístup k vašemu zdroji, nemají žádný způsob, jak si poznáte, že jejich kód vyžaduje **RegistryPermission** , aby mohl váš kód použít. V takovém případě, pokud se rozhodnete, že není přiměřené nebo nutné vyžadovat, aby volající vašeho kódu měli oprávnění pro přístup do registru, můžete uplatnit oprávnění pro čtení registru. V této situaci je vhodné, aby knihovna mohla uplatnit oprávnění, aby volající bez **RegistryPermission** mohli použít knihovnu.  
  
 Kontrolní výraz ovlivňuje procházení zásobníku pouze v případě, že kontrolní oprávnění a oprávnění vyžádané volajícím jsou stejného typu a pokud je požadované oprávnění podmnožinou vyžádaného oprávnění. Například, pokud vyberete hodnotu **FileIOPermission** pro čtení všech souborů na jednotce C a pro datové jednotky **FileIOPermission** se provede požadavek na přečtení souborů v C:\Temp, může kontrolní výraz ovlivnit procházení zásobníku. Nicméně pokud byla poptávka pro **FileIOPermission** pro zápis do jednotky C, kontrolní výraz by neměl mít žádný vliv.  
  
 Chcete-li provést kontrolní výrazy, váš kód musí mít udělené oprávnění a <xref:System.Security.Permissions.SecurityPermission> , které představuje právo k provedení kontrolního výrazu. I když byste mohli vyhodnotit oprávnění, že váš kód nebyl udělen, kontrolní výraz by byl bezúčelné, protože ověření zabezpečení by mohlo selhat předtím, než může kontrolní výraz způsobit jeho úspěch.  
  
 Následující ilustrace ukazuje, co se stane, když použijete **Assert**. Předpokládejme, že následující příkazy jsou pravdivé pro sestavení A, B, C, E a F a dvě oprávnění, P1 a P1A:  
  
- P1A představuje právo číst soubory. txt na jednotce C.  
  
- P1 představuje právo na čtení všech souborů na jednotce C.  
  
- P1A a P1 jsou oba typy **FileIOPermission** a je P1A podmnožinou P1.  
  
- Sestavením E a F byla udělena oprávnění P1A.  
  
- Sestavení C bylo uděleno oprávnění P1.  
  
- Sestavení A a B byla udělena oprávnění P1 ani P1A.  
  
- Metoda A je obsažena v sestavení A, metoda B je obsažena v sestavení B a tak dále.  
  
 ![Diagram, který znázorňuje sestavení metody Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)    
  
 V tomto scénáři volá metoda A volání B, B volání jazyka C, volání jazyka C E a E volá F. Metoda C kontrolní výrazy oprávnění ke čtení souborů na jednotce C (oprávnění P1) a metoda E požaduje oprávnění ke čtení souborů. txt na jednotce C (oprávnění P1A). V případě, že poptávka v F je zjištěna v době běhu, je provedeno procházení zásobníku pro kontrolu oprávnění všech volajících F, počínaje E. E byl uděleno oprávnění P1A, takže procházení zásobníku pokračuje v kontrole oprávnění jazyka C, kde je zjištěn kontrolní výraz C. Vzhledem k tomu, že vyžádané oprávnění (P1A) je podmnožinou vyžádaného oprávnění (P1), procházení zásobníku se zastaví a Automatická kontroly zabezpečení se nezdaří. Nezáleží na tom, že sestavení A a B nemají udělena oprávnění P1A. Vytvrzením P1, metoda C zaručí, že volající mají přístup k prostředku chráněnému P1, a to i v případě, že volajícímu nebylo uděleno oprávnění k přístupu k tomuto prostředku.  
  
 Pokud navrhujete knihovnu tříd a třída přistupuje k chráněnému prostředku, měli byste ve většině případů učinit požadavek zabezpečení vyžadující, aby volající třídy měly příslušné oprávnění. Pokud třída pak provede operaci, pro kterou víte, že většina volajících nebude mít oprávnění, a pokud jste ochotni vzít zodpovědnost za to, že volajícímu kódu zavoláte, můžete toto oprávnění uplatnit voláním metody **Assert** na objekt oprávnění, který představuje operaci, kterou kód provádí. Použití **výrazu Assert** tímto způsobem umožňuje volajícím, které obvykle nemohou provést volání vašeho kódu. Proto pokud přiřadíte oprávnění, měli byste předem provést příslušné kontroly zabezpečení, aby nedošlo k nesprávnému použití vaší komponenty.  
  
 Předpokládejme například, že vaše vysoce důvěryhodná třída knihovny má metodu, která odstraňuje soubory. Přistupuje k souboru voláním nespravované funkce Win32. Volající vyvolá metodu **odstranění** kódu předáním názvu souboru, který má být odstraněn, C:\Test.txt. V rámci metody **Delete** váš kód vytvoří objekt, <xref:System.Security.Permissions.FileIOPermission> který představuje přístup pro zápis do C:\Test.txt. (K odstranění souboru se vyžaduje přístup pro zápis.) Váš kód poté vyvolá imperativní kontrolu zabezpečení voláním metody **Demand** objektu **FileIOPermission** . Pokud jedno z volajících v zásobníku volání nemá toto oprávnění, <xref:System.Security.SecurityException> je vyvolána výjimka. Pokud není vyvolána žádná výjimka, víte, že všichni volající mají právo na přístup k C:\Test.txt. Vzhledem k tomu, že většina vašich volajících nebude mít oprávnění pro přístup k nespravovanému kódu, váš kód pak <xref:System.Security.Permissions.SecurityPermission> vytvoří objekt, který představuje právo na volání nespravovaného kódu a volá metodu **Assert** objektu. Nakonec volá nespravovanou funkci Win32 k odstranění C:\Text.txt a vrátí řízení volajícímu.  
  
> [!CAUTION]
>  Musíte mít jistotu, že váš kód nepoužívá kontrolní výrazy v situacích, kdy váš kód může být použit jiným kódem pro přístup k prostředku, který je chráněn oprávněním, které uplatňujete. Například v kódu, který zapisuje do souboru, jehož název je zadán volajícím jako parametr, neurčíte hodnotu **FileIOPermission** pro zápis do souborů, protože kód by byl otevřen pro zneužití třetí stranou.  
  
 Při použití imperativní syntaxe zabezpečení volání metody **Assert** u více oprávnění ve stejné metodě způsobí vyvolání výjimky zabezpečení. Místo toho byste měli vytvořit objekt **PermissionSet** , předat jeho jednotlivá oprávnění, která chcete vyvolat, a pak zavolat metodu **Assert** na objekt **PermissionSet** . Metodu **Assert** můžete zavolat více než jednou, pokud použijete deklarativní syntaxi zabezpečení.  
  
 Následující příklad ukazuje deklarativní syntaxi pro přepsání kontrol zabezpečení pomocí metody **Assert** . Všimněte si, že syntaxe **FileIOPermissionAttribute** přebírá dvě hodnoty <xref:System.Security.Permissions.SecurityAction> : výčet a umístění souboru nebo adresáře, ke kterému má být uděleno oprávnění. Volání metody **Assert** způsobí, že požadavky pro přístup `C:\Log.txt` budou úspěšné, i když volajícím nejsou kontrolováni oprávnění k přístupu k souboru.  
  
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
  
 Následující fragmenty kódu ukazují imperativní syntaxi pro přepsání kontrol zabezpečení pomocí metody **Assert** . V tomto příkladu je deklarována instance objektu **FileIOPermission** . Jeho konstruktoru je předán **FileIOPermissionAccess. AllAccess** , který definuje typ povoleného přístupu následovaný řetězcem, který popisuje umístění souboru. Po definování objektu **FileIOPermission** stačí volat jeho metodu **Assert** pro přepsání kontroly zabezpečení.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [Atributy](../../standard/attributes/index.md)
- [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)
