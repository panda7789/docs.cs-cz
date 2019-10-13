---
title: 'Postupy: ukládání asymetrických klíčů v kontejneru klíčů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET Framework]
- encryption [.NET Framework], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8edb88d13732650e00292d63ad4e1975a97ac704
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291639"
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="9f658-102">Postupy: ukládání asymetrických klíčů v kontejneru klíčů</span><span class="sxs-lookup"><span data-stu-id="9f658-102">How to: Store Asymmetric Keys in a Key Container</span></span>
<span data-ttu-id="9f658-103">Asymetrické privátní klíče by nikdy neměly být uložené v místním počítači do doslovného znění ani do prostého textu.</span><span class="sxs-lookup"><span data-stu-id="9f658-103">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="9f658-104">Pokud potřebujete uložit privátní klíč, měli byste použít kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="9f658-104">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="9f658-105">Další informace o kontejnerech klíčů najdete v tématu [Principy kontejnerů klíčů RSA na úrovni počítače a na úrovni uživatele](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9f658-105">For more information on key containers, see [Understanding Machine-Level and User-Level RSA Key Containers](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span></span>  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="9f658-106">Vytvoření asymetrického klíče a jeho uložení do kontejneru klíčů</span><span class="sxs-lookup"><span data-stu-id="9f658-106">To create an asymmetric key and save it in a key container</span></span>  
  
1. <span data-ttu-id="9f658-107">Vytvořte novou instanci třídy <xref:System.Security.Cryptography.CspParameters> a předejte název, který chcete volat kontejner klíčů, do pole <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9f658-107">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>  
  
2. <span data-ttu-id="9f658-108">Vytvořte novou instanci třídy, která je odvozena z třídy <xref:System.Security.Cryptography.AsymmetricAlgorithm> (obvykle **RSACryptoServiceProvider** nebo **DSACryptoServiceProvider**) a předejte dříve vytvořený objekt **CspParameters** konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="9f658-108">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
### <a name="to-delete-the-key-from-a-key-container"></a><span data-ttu-id="9f658-109">Odstranění klíče z kontejneru klíčů</span><span class="sxs-lookup"><span data-stu-id="9f658-109">To delete the key from a key container</span></span>  
  
1. <span data-ttu-id="9f658-110">Vytvořte novou instanci třídy **CspParameters** a předejte název, který chcete zavolat kontejneru klíčů do pole **CspParameters. ContainerName** .</span><span class="sxs-lookup"><span data-stu-id="9f658-110">Create a new instance of a **CspParameters** class and pass the name that you want to call the key container to the **CspParameters.KeyContainerName** field.</span></span>  
  
2. <span data-ttu-id="9f658-111">Vytvoří novou instanci třídy, která je odvozena z třídy **AsymmetricAlgorithm** (obvykle **RSACryptoServiceProvider** nebo **DSACryptoServiceProvider**) a předá dříve vytvořený objekt **CspParameters** do konstruktoru. .</span><span class="sxs-lookup"><span data-stu-id="9f658-111">Create a new instance of a class that derives from the **AsymmetricAlgorithm** class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
3. <span data-ttu-id="9f658-112">Nastavte vlastnost **PersistKeyInCsp** třídy, která je odvozena z **AsymmetricAlgorithm** na **false** (**false** v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="9f658-112">Set the **PersistKeyInCSP** property of the class that derives from **AsymmetricAlgorithm** to **false** (**False** in Visual Basic).</span></span>  
  
4. <span data-ttu-id="9f658-113">Zavolejte metodu **clear** třídy, která je odvozena z **AsymmetricAlgorithm**.</span><span class="sxs-lookup"><span data-stu-id="9f658-113">Call the **Clear** method of the class that derives from **AsymmetricAlgorithm**.</span></span> <span data-ttu-id="9f658-114">Tato metoda uvolní všechny prostředky třídy a vymaže kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="9f658-114">This method releases all resources of the class and clears the key container.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f658-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9f658-115">Example</span></span>  
 <span data-ttu-id="9f658-116">Následující příklad ukazuje, jak vytvořit asymetrický klíč, uložit ho do kontejneru klíčů, načíst klíč později a odstranit klíč z kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9f658-116">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>  
  
 <span data-ttu-id="9f658-117">Všimněte si, že kód v metodě `GenKey_SaveInContainer` a v metodě `GetKeyFromContainer` je podobný.</span><span class="sxs-lookup"><span data-stu-id="9f658-117">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span>  <span data-ttu-id="9f658-118">Když zadáte název kontejneru klíčů pro objekt @no__t 0 a předáte ho do objektu <xref:System.Security.Cryptography.AsymmetricAlgorithm> s vlastností <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> nebo vlastností <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> nastavenou na hodnotu true, dojde k následujícímu:</span><span class="sxs-lookup"><span data-stu-id="9f658-118">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to true, the following occurs.</span></span>  <span data-ttu-id="9f658-119">Pokud kontejner klíčů se zadaným názvem neexistuje, vytvoří se a klíč se uloží.</span><span class="sxs-lookup"><span data-stu-id="9f658-119">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>  <span data-ttu-id="9f658-120">Pokud existuje kontejner klíčů se zadaným názvem, klíč v kontejneru se automaticky načte do aktuálního objektu <xref:System.Security.Cryptography.AsymmetricAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="9f658-120">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>  <span data-ttu-id="9f658-121">Proto kód v metodě `GenKey_SaveInContainer` uchovává klíč, protože je spuštěn jako první, zatímco kód v metodě `GetKeyFromContainer` načte klíč, protože se spustí sekunda.</span><span class="sxs-lookup"><span data-stu-id="9f658-121">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it is run second.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
 _  
  
Public Class StoreKey  
  
    Public Shared Sub Main()  
        Try  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
        Catch e As CryptographicException  
            Console.WriteLine(e.Message)  
        End Try  
    End Sub  
  
    Public Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        ' name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key added to container:  {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub GetKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Delete the key entry in the container.  
        rsa.PersistKeyInCsp = False  
  
        ' Call Clear to release resources and delete the key from the container.  
        rsa.Clear()  
  
        Console.WriteLine("Key deleted.")  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
  
public class StoreKey  
  
{  
    public static void Main()  
    {  
        try  
        {  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
        }  
        catch(CryptographicException e)  
        {  
            Console.WriteLine(e.Message);  
        }  
  
    }  
  
    public static void GenKey_SaveInContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key added to container: \n  {0}", rsa.ToXmlString(true));  
    }  
  
    public static void GetKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : \n {0}", rsa.ToXmlString(true));  
    }  
  
    public static void DeleteKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Delete the key entry in the container.  
        rsa.PersistKeyInCsp = false;  
  
        // Call Clear to release resources and delete the key from the container.  
        rsa.Clear();  
  
        Console.WriteLine("Key deleted.");  
    }  
}  
```  
  
```console  
Key added to container:  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key retrieved from container :  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key deleted.  
Key added to container:  
<RSAKeyValue> Key Information B</RSAKeyValue>  
Key deleted.  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f658-122">Další informace najdete v tématech</span><span class="sxs-lookup"><span data-stu-id="9f658-122">See also</span></span>

- [<span data-ttu-id="9f658-123">Generování klíčů pro šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="9f658-123">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="9f658-124">Šifrování dat</span><span class="sxs-lookup"><span data-stu-id="9f658-124">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)
- [<span data-ttu-id="9f658-125">Dešifrování dat</span><span class="sxs-lookup"><span data-stu-id="9f658-125">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)
- [<span data-ttu-id="9f658-126">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="9f658-126">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
