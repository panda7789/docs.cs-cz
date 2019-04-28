---
title: 'Postupy: Přiřazení uživatelských informací pro seskupení připojení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ce550d6-8f7c-4ea7-add8-5bc27a7b51be
ms.openlocfilehash: 2fa84052bcf9ca97b903111fc02e319b25deb384
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642708"
---
# <a name="how-to-assign-user-information-to-group-connections"></a><span data-ttu-id="7f804-102">Postupy: Přiřazení uživatelských informací pro seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="7f804-102">How to: Assign User Information to Group Connections</span></span>

 <span data-ttu-id="7f804-103">Následující příklad ukazuje, jak se přiřazení uživatelských informací pro seskupení připojení, za předpokladu, že aplikace nastaví proměnné *uživatelské jméno*, *SecurelyStoredPassword*, a  *Domény* před voláním této části kódu a který *uživatelské jméno* je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="7f804-103">The following example demonstrates how to assign user information to group connections, assuming that the application sets the variables *UserName*, *SecurelyStoredPassword*, and *Domain* before this section of code is called and that *UserName* is unique.</span></span>  
  
### <a name="to-assign-user-information-to-a-group-connection"></a><span data-ttu-id="7f804-104">Informace o uživateli přiřadit skupiny připojení</span><span class="sxs-lookup"><span data-stu-id="7f804-104">To assign user information to a group connection</span></span>  
  
1. <span data-ttu-id="7f804-105">Vytvoření názvu skupiny připojení.</span><span class="sxs-lookup"><span data-stu-id="7f804-105">Create a connection group name.</span></span>  
  
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
  
2. <span data-ttu-id="7f804-106">Vytvořte požadavek na konkrétní adresu URL.</span><span class="sxs-lookup"><span data-stu-id="7f804-106">Create a request for a specific URL.</span></span> <span data-ttu-id="7f804-107">Například následující kód vytvoří žádost pro adresu URL `http://www.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="7f804-107">For example, the following code creates a request for the URL `http://www.contoso.com.`</span></span>  
  
    ```csharp  
    WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
    ```  
  
    ```vb  
    Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ```  
  
3. <span data-ttu-id="7f804-108">Nastavit přihlašovací údaje a připojení GroupName pro webové žádosti a volání **GetResponse** k načtení **WebResponse** objektu.</span><span class="sxs-lookup"><span data-stu-id="7f804-108">Set the credentials and Connection GroupName for the Web request, and call **GetResponse** to retrieve a **WebResponse** object.</span></span>  
  
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
  
4. <span data-ttu-id="7f804-109">Zavřete datový proud odpovědí po použití WebRespose objektu.</span><span class="sxs-lookup"><span data-stu-id="7f804-109">Close the response stream after using the WebRespose object.</span></span>  
  
    ```csharp  
    MyWebResponse.Close();  
    ```  
  
    ```vb  
    MyWebResponse.Close()  
    ```  
  
 <span data-ttu-id="7f804-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f804-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f804-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f804-111">See also</span></span>

- [<span data-ttu-id="7f804-112">Správa připojení</span><span class="sxs-lookup"><span data-stu-id="7f804-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)
- [<span data-ttu-id="7f804-113">Seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="7f804-113">Connection Grouping</span></span>](../../../docs/framework/network-programming/connection-grouping.md)
