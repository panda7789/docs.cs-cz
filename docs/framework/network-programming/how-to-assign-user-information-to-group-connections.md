---
title: 'Postupy: přiřazení uživatelských informací pro seskupení připojení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ce550d6-8f7c-4ea7-add8-5bc27a7b51be
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 009c23d0015f366ab5f1ee92609f0131465d827b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193095"
---
# <a name="how-to-assign-user-information-to-group-connections"></a><span data-ttu-id="41892-102">Postupy: přiřazení uživatelských informací pro seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="41892-102">How to: Assign User Information to Group Connections</span></span>

  
 <span data-ttu-id="41892-103">Následující příklad ukazuje, jak se přiřazení uživatelských informací pro seskupení připojení, za předpokladu, že aplikace nastaví proměnné *uživatelské jméno*, *SecurelyStoredPassword*, a  *Domény* před voláním této části kódu a který *uživatelské jméno* je jedinečný.</span><span class="sxs-lookup"><span data-stu-id="41892-103">The following example demonstrates how to assign user information to group connections, assuming that the application sets the variables *UserName*, *SecurelyStoredPassword*, and *Domain* before this section of code is called and that *UserName* is unique.</span></span>  
  
### <a name="to-assign-user-information-to-a-group-connection"></a><span data-ttu-id="41892-104">Informace o uživateli přiřadit skupiny připojení</span><span class="sxs-lookup"><span data-stu-id="41892-104">To assign user information to a group connection</span></span>  
  
1.  <span data-ttu-id="41892-105">Vytvoření názvu skupiny připojení.</span><span class="sxs-lookup"><span data-stu-id="41892-105">Create a connection group name.</span></span>  
  
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
  
2.  <span data-ttu-id="41892-106">Vytvořte požadavek na konkrétní adresu URL.</span><span class="sxs-lookup"><span data-stu-id="41892-106">Create a request for a specific URL.</span></span> <span data-ttu-id="41892-107">Například následující kód vytvoří žádost pro adresu URL `http://www.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="41892-107">For example, the following code creates a request for the URL `http://www.contoso.com.`</span></span>  
  
    ```csharp  
    WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
    ```  
  
    ```vb  
    Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ```  
  
3.  <span data-ttu-id="41892-108">Nastavit přihlašovací údaje a připojení GroupName pro webové žádosti a volání **GetResponse** k načtení **WebResponse** objektu.</span><span class="sxs-lookup"><span data-stu-id="41892-108">Set the credentials and Connection GroupName for the Web request, and call **GetResponse** to retrieve a **WebResponse** object.</span></span>  
  
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
  
4.  <span data-ttu-id="41892-109">Zavřete datový proud odpovědí po použití WebRespose objektu.</span><span class="sxs-lookup"><span data-stu-id="41892-109">Close the response stream after using the WebRespose object.</span></span>  
  
    ```csharp  
    MyWebResponse.Close();  
    ```  
  
    ```vb  
    MyWebResponse.Close()  
    ```  
  
 <span data-ttu-id="41892-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="41892-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="41892-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="41892-111">See Also</span></span>  
 [<span data-ttu-id="41892-112">Správa připojení</span><span class="sxs-lookup"><span data-stu-id="41892-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)  
 [<span data-ttu-id="41892-113">Seskupení připojení</span><span class="sxs-lookup"><span data-stu-id="41892-113">Connection Grouping</span></span>](../../../docs/framework/network-programming/connection-grouping.md)
