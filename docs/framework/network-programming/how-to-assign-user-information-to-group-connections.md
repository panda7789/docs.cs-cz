---
title: 'Postupy: Přiřazení uživatelských informací pro seskupení připojení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ce550d6-8f7c-4ea7-add8-5bc27a7b51be
ms.openlocfilehash: 8e104de891d72e709ae20055737540516109da68
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048429"
---
# <a name="how-to-assign-user-information-to-group-connections"></a><span data-ttu-id="363bf-102">Postupy: Přiřazení uživatelských informací pro seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="363bf-102">How to: Assign User Information to Group Connections</span></span>

 <span data-ttu-id="363bf-103">Následující příklad ukazuje, jak přiřadit informace o uživateli pro seskupení připojení, za předpokladu, že aplikace nastaví proměnné *username*, *securelyStoredPassword*a *Domain* před voláním této části kódu a *Uživatelské jméno* je jedinečné.</span><span class="sxs-lookup"><span data-stu-id="363bf-103">The following example demonstrates how to assign user information to group connections, assuming that the application sets the variables *UserName*, *SecurelyStoredPassword*, and *Domain* before this section of code is called and that *UserName* is unique.</span></span>  
  
### <a name="to-assign-user-information-to-a-group-connection"></a><span data-ttu-id="363bf-104">Přiřazení informací o uživateli k připojení skupiny</span><span class="sxs-lookup"><span data-stu-id="363bf-104">To assign user information to a group connection</span></span>  
  
1. <span data-ttu-id="363bf-105">Vytvořte název skupiny připojení.</span><span class="sxs-lookup"><span data-stu-id="363bf-105">Create a connection group name.</span></span>  
  
    ```csharp  
    SHA1Managed Sha1 = new SHA1Managed();  
    Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
    String secureGroupName = Encoding.Default.GetString(updHash);  
    ```  
  
    ```vb  
    Dim Sha1 As New SHA1Managed()  
    Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
    Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
    ```  
  
2. <span data-ttu-id="363bf-106">Vytvoří požadavek na konkrétní adresu URL.</span><span class="sxs-lookup"><span data-stu-id="363bf-106">Create a request for a specific URL.</span></span> <span data-ttu-id="363bf-107">Například následující kód vytvoří požadavek na adresu URL.`http://www.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="363bf-107">For example, the following code creates a request for the URL `http://www.contoso.com.`</span></span>  
  
    ```csharp  
    WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
    ```  
  
    ```vb  
    Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ```  
  
3. <span data-ttu-id="363bf-108">Nastavte přihlašovací údaje a název_skupiny připojení pro webový požadavek a zavolejte **GetResponse** k načtení objektu **WebResponse** .</span><span class="sxs-lookup"><span data-stu-id="363bf-108">Set the credentials and Connection GroupName for the Web request, and call **GetResponse** to retrieve a **WebResponse** object.</span></span>  
  
    ```csharp  
    myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);   
    myWebRequest.ConnectionGroupName = secureGroupName;  
  
    WebResponse myWebResponse=myWebRequest.GetResponse();  
    ```  
  
    ```vb  
    myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
    myWebRequest.ConnectionGroupName = secureGroupName  
  
    Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
    ```  
  
4. <span data-ttu-id="363bf-109">Po použití objektu WebRespose zavřete datový proud odpovědi.</span><span class="sxs-lookup"><span data-stu-id="363bf-109">Close the response stream after using the WebRespose object.</span></span>  
  
    ```csharp  
    MyWebResponse.Close();  
    ```  
  
    ```vb  
    MyWebResponse.Close()  
    ```  
  
 <span data-ttu-id="363bf-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="363bf-110">Example</span></span>  
  
```csharp  
// Create a connection group name.  
SHA1Managed Sha1 = new SHA1Managed();  
Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
String secureGroupName = Encoding.Default.GetString(updHash);  
  
// Create a request for a specific URL.  
WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
  
myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);   
myWebRequest.ConnectionGroupName = secureGroupName;  
  
WebResponse myWebResponse=myWebRequest.GetResponse();  
  
// Insert the code that uses myWebResponse.  
  
MyWebResponse.Close();  
```  
  
```vb  
' Create a secure group name.  
Dim Sha1 As New SHA1Managed()  
Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
  
' Create a request for a specific URL.  
Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
  
myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
myWebRequest.ConnectionGroupName = secureGroupName  
  
Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
  
' Insert the code that uses myWebResponse.  
MyWebResponse.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="363bf-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="363bf-111">See also</span></span>

- [<span data-ttu-id="363bf-112">Správa připojení</span><span class="sxs-lookup"><span data-stu-id="363bf-112">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="363bf-113">Seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="363bf-113">Connection Grouping</span></span>](connection-grouping.md)
