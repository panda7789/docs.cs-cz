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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f040e1e1706e1f84ced8b253ff3fb15dbcbd6e1e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206019"
---
# <a name="link-demands"></a>Požadavky na odkaz
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Požadavek propojení způsobí kontrolu zabezpečení během kompilace za běhu a kontroluje pouze okamžité volání sestavení kódu. Propojení nastane, pokud je váš kód svázán s odkazem na typ, včetně odkazů na ukazatel funkce a volání metod. Pokud volající sestavení nemá dostatečná oprávnění pro odkazování na váš kód, není odkaz povolen a výjimka za běhu je vyvolána, když je kód načten a spuštěn. Požadavky na propojení lze přepsat v třídách, které dědí z vašeho kódu.  
  
 Všimněte si, že se s tímto typem požadavku neprovádí kompletní procházení zásobníku a že váš kód je stále náchylný k luring útokům. Například pokud je metoda v sestavení A chráněna požadavkem propojení, je přímý volající v sestavení B vyhodnocován na základě oprávnění sestavení B.  Požadavek propojení však nevyhodnotí metodu v sestavení C, pokud nepřímo volá metodu v sestavení A pomocí metody v sestavení B. Požadavek propojení určuje pouze oprávnění přímí volající v bezprostředním volajícím sestavení musí mít odkaz na váš kód. Neurčuje oprávnění, která všichni volající musí mít ke spuštění kódu.  
  
 Modifikátory <xref:System.Security.CodeAccessPermission.Deny%2A>procházení zásobníku <xref:System.Security.CodeAccessPermission.PermitOnly%2A> , a nejsou ovlivněny vyhodnocením požadavků propojení. <xref:System.Security.CodeAccessPermission.Assert%2A>  Vzhledem k tomu, že požadavky na propojení neprovádějí procházení zásobníku, modifikátory procházení zásobníku nemají žádný vliv na požadavky propojení.  
  
 Pokud je metoda chráněná požadavkem propojení k dispozici [](../reflection-and-codedom/reflection.md)prostřednictvím reflexe, pak požadavek na propojení zkontroluje bezprostředního volajícího kódu, ke kterému se přistupoval prostřednictvím reflexe. To platí jak pro zjišťování metod, tak pro volání metod prováděná pomocí reflexe. Předpokládejme například, že kód používá reflexi k <xref:System.Reflection.MethodInfo> vrácení objektu, který představuje metodu chráněnou požadavkem propojení a poté předá tento objekt **MethodInfo** do nějakého jiného kódu, který používá objekt k vyvolání původní metody. V tomto případě proběhne ověření požadavku propojení dvakrát: jednou pro kód, který vrátí objekt **MethodInfo** a jednou pro kód, který ho vyvolá.  
  
> [!NOTE]
> Požadavek propojení prováděný u konstruktoru statické třídy nechrání konstruktor, protože statické konstruktory jsou volány systémem, mimo cestu spuštění kódu aplikace. V důsledku toho, pokud je požadavek na propojení aplikován na celou třídu, nemůže chránit přístup ke statickému konstruktoru, i když chrání zbytek třídy.  
  
 Následující fragment kódu deklarativně určuje, že jakýkoli kód spojující `ReadData` metodu musí `CustomPermission` mít oprávnění. Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v .NET Framework. Požadavek je proveden předáním příznaku **SecurityAction. LinkDemand** do `CustomPermissionAttribute`.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Atributy](../../standard/attributes/index.md)
- [Zabezpečení přístupu kódu](code-access-security.md)
