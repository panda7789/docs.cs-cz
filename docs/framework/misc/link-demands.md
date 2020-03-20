---
title: Požadavky na odkaz
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
ms.openlocfilehash: a0466eb5c24840c77a3b191f9b0e001f6b267fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181164"
---
# <a name="link-demands"></a>Požadavky na odkaz
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Požadavek na propojení způsobí kontrolu zabezpečení během kompilace just-in-time a zkontroluje pouze okamžité volající sestavení vašeho kódu. K propojení dochází, když je váš kód vázán na odkaz na typ, včetně odkazů na ukazatel funkce a volání metody. Pokud volající sestavení nemá dostatečná oprávnění k propojení s vaším kódem, odkaz není povolen a při načtení a spuštění kódu je vyvolána výjimka za běhu. Požadavky na propojení mohou být přepsány ve třídách, které dědí z vašeho kódu.  
  
 Všimněte si, že úplné procházení zásobníku se neprovádí s tímto typem poptávky a že váš kód je stále náchylný k lákavým útokům. Například pokud je metoda v sestavení A chráněna požadavkem na propojení, je vyhodnocen přímý volající v sestavení B na základě oprávnění sestavení B.  Požadavek na propojení však nevyhodnotí metodu v sestavení C, pokud nepřímo volá metodu v sestavení A pomocí metody v sestavení B. Požadavek na propojení určuje pouze oprávnění, která musí mít přímí volající v sestavení okamžitého volání k propojení s vaším kódem. Neurčuje oprávnění, která musí mít všichni volající ke spuštění kódu.  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>Modifikátory procházení a <xref:System.Security.CodeAccessPermission.PermitOnly%2A> procházení zásobníku nemají vliv na vyhodnocení požadavků na <xref:System.Security.CodeAccessPermission.Deny%2A>propojení.  Vzhledem k tomu, že požadavky na propojení neprovádějí procházení zásobníku, modifikátory procházení zásobníku nemají žádný vliv na požadavky na propojení.  
  
 Pokud metoda chráněná požadavek propojení je přístupná prostřednictvím [reflexe](../reflection-and-codedom/reflection.md), pak požadavek na propojení zkontroluje okamžitévolající kódu přistupovat prostřednictvím reflexe. To platí jak pro zjišťování metody a pro vyvolání metody provádí pomocí reflexe. Předpokládejme například, že kód <xref:System.Reflection.MethodInfo> používá reflexi k vrácení objektu představujícího metodu chráněnou požadavkem na propojení a poté předá tento objekt **MethodInfo** jinému kódu, který používá objekt k vyvolání původní metody. V tomto případě dojde ke kontrole poptávky propojení dvakrát: jednou pro kód, který vrací Objekt **MethodInfo** a jednou pro kód, který jej vyvolá.  
  
> [!NOTE]
> Požadavek na propojení prováděný na konstruktoru statické třídy nechrání konstruktor, protože statické konstruktory jsou volány systémem mimo cestu spuštění kódu aplikace. V důsledku toho při použití požadavku propojení na celou třídu, nemůže chránit přístup ke statickékonstruktoru, i když chrání zbytek třídy.  
  
 Následující fragment kódu deklarativně určuje, `ReadData` že jakýkoli `CustomPermission` kód odkazující na metodu musí mít oprávnění. Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v rozhraní .NET Framework. Požadavek je proveden předáním příznaku **SecurityAction.LinkDemand** na `CustomPermissionAttribute`.  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Atributy](../../standard/attributes/index.md)
- [Zabezpečení přístupu kódu](code-access-security.md)
