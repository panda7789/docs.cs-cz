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
ms.openlocfilehash: 2ba3172b1a82c0a9f624a49eb63a193dd29faac1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166983"
---
# <a name="link-demands"></a>Požadavky na odkaz
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Požadavek na propojení způsobí, že kontrola zabezpečení během kompilace just-in-time a zkontroluje pouze okamžitého volajícího sestavení vašeho kódu. Propojení nastane, pokud váš kód je vázán na odkaz na typ, včetně odkazů na ukazatel funkce a volání metody. Pokud volající sestavení nemá dostatečná oprávnění k propojení vašeho kódu, na odkaz není povolen a je vyvolána výjimka za běhu, když je načten a spustit kód. Požadavky propojení lze přepsat ve třídách, které dědí z vašeho kódu.  
  
 Všimněte si, že se neprovede úplné zásobníku s tímto typem vyžádání a že váš kód je přesto náchylné k útokům luring. Například pokud metodu v sestavení A je chráněn pomocí požadavku propojení, přímému volajícímu v sestavení B je vyhodnotí na základě oprávnění sestavení B.  Ale požadavek propojení nebude vyhodnotit metodu v sestavení C nepřímo volá metodu v sestavení pomocí metody v sestavení B. Požadavek propojení určuje že jenom oprávnění přímý volající v okamžitého volajícího sestavení musí mít odkaz na váš kód. Neurčuje oprávnění všichni volající musí mít pro spouštění vašeho kódu.  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, A <xref:System.Security.CodeAccessPermission.PermitOnly%2A> zásobníku funkce walk modifikátory nemají vliv na hodnocení požadavků propojení.  Protože požadavky propojení neprovádějte procházení zásobníku, modifikátory procházení zásobníku nemají žádný vliv na požadavky propojení.  
  
 Pokud metoda chráněn pomocí požadavku propojení je přístupný prostřednictvím [reflexe](../../../docs/framework/reflection-and-codedom/reflection.md), pak požadavek propojení kontroluje okamžitého volajícího kódu přístupné prostřednictvím reflexe. To platí pro metody zjišťování a pro volání metody provést pomocí operace reflection. Předpokládejme například, že kód používá reflexi se vraťte <xref:System.Reflection.MethodInfo> objekt představující metodu chráněn pomocí požadavku propojení a potom předává, který **MethodInfo** objektu na jiný kód, který používá objekt volání původní metody. V tomto případě ověření požadavku propojení dojde k dvakrát: jednou pro kód, který vrátí **MethodInfo** objekt a jednou pro kód, který vyvolá ji.  
  
> [!NOTE]
>  Požadavek propojení provést ve statickém konstruktoru třídy nechrání konstruktoru, protože statické konstruktory jsou volány aplikací systému mimo cesta provádění kódu vaší aplikace. V důsledku toho při požadavku na propojení platí pro celou třídu, nemůže chránit přístup k statický konstruktor, přestože chrání zbytek třídy.  
  
 Následující fragment kódu deklarativně určuje, že jakékoli propojení do kódu `ReadData` metoda musí mít `CustomPermission` oprávnění. Toto oprávnění je hypotetický vlastní oprávnění a neexistuje v rozhraní .NET Framework. Předáním je vznesen požadavek **SecurityAction.LinkDemand** příznak, který `CustomPermissionAttribute`.  
  
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

- [Atributy](../../../docs/standard/attributes/index.md)
- [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)
