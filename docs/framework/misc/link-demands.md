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
ms.openlocfilehash: 29a3254bb5ccfe422a1c2d7d156975c0887d9273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390660"
---
# <a name="link-demands"></a>Požadavky na odkaz
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Požadavek propojení způsobí, že kontrola zabezpečení během kompilace za běhu a zkontroluje pouze okamžité volání sestavení vašeho kódu. Propojování nastane, když kód je vázána na odkaz na typ, včetně odkazů ukazatel funkce a volání metod. Pokud volajícího sestavení nemá dostatečná oprávnění k propojení kódu, není povolena na odkaz a výjimku modulu runtime je vyvolána, pokud kód je načíst a spustit. Požadavky na odkaz může být přepsána nastaveními v tříd, které dědí z vašeho kódu.  
  
 Všimněte si, že s tímto typem vyžádání neprovádí se procházení úplné zásobníku a váš kód je přesto náchylné k útokům luring. Například pokud metoda v sestavení A chráněn požadavek propojení, přímý volající v sestavení B je vyhodnotit na základě oprávnění sestavení B.  Požadavek propojení však nevyhodnotí metodu v sestavení C, pokud nepřímo volá metodu v sestavení pomocí metody v sestavení B. Požadavek propojení určuje, že pouze oprávnění přímých volajících v okamžité volání sestavení musí mít k propojení kódu. Neurčuje oprávnění všechny volající musí mít pro spouštění vašeho kódu.  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, A <xref:System.Security.CodeAccessPermission.PermitOnly%2A> modifikátory průchodu zásobníkem neovlivní hodnocení požadavků propojení.  Protože požadavky na odkaz neprovádět procházení zásobníku, Modifikátory průchodu zásobníkem nemají žádný vliv na požadavky na odkaz.  
  
 Pokud je metoda chráněna požadavkem propojení přistupuje prostřednictvím [reflexe](../../../docs/framework/reflection-and-codedom/reflection.md), pak požadavek propojení zkontroluje bezprostředního volajícího kódu přistupovat prostřednictvím reflexe. To platí pro metody zjišťování i pro volání metody provést pomocí reflexe. Předpokládejme například, že kód používá reflexe vrátit <xref:System.Reflection.MethodInfo> objekt představující metodu chráněnou požadavkem propojení a potom předá který **MethodInfo** objekt, který má jiný kód, který používá objekt k vyvolání původní metody. V takovém případě ověření požadavku propojení nastane dvakrát: jednou pro kód, který vrátí **MethodInfo** objekt a jednou pro kód, který vyvolá ho.  
  
> [!NOTE]
>  Požadavek propojení v konstruktoru statická třída provést nechrání konstruktoru, protože statické konstruktory jsou volány systému mimo cestu provádění kódu aplikace. V důsledku toho při požadavku na propojení k celou třídu, nelze chránit přístup k statického konstruktoru, přestože chrání zbytek třídy.  
  
 Následující fragment kódu deklarativně určuje, že jakékoli propojení do kódu `ReadData` metoda musí mít `CustomPermission` oprávnění. Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v rozhraní .NET Framework. Požadavek je vytvořen pomocí předání **SecurityAction.LinkDemand** příznak, který `CustomPermissionAttribute`.  
  
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
 [Atributy](../../../docs/standard/attributes/index.md)  
 [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)
