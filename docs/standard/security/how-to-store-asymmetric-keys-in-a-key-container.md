---
title: 'Postupy: Uložení asymetrického klíče v kontejneru klíčů'
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
ms.openlocfilehash: a5cd157f89797406fbe87c3d70c415d7b192d1a9
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746442"
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="a9d50-102">Postupy: Uložení asymetrického klíče v kontejneru klíčů</span><span class="sxs-lookup"><span data-stu-id="a9d50-102">How to: Store Asymmetric Keys in a Key Container</span></span>
<span data-ttu-id="a9d50-103">Asymetrické soukromé klíče by nikdy neměly být uloženy doslovně nebo ve formátu prostého textu v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="a9d50-103">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="a9d50-104">Pokud potřebujete uložit soukromý klíč, měli byste použít kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="a9d50-104">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="a9d50-105">Další informace o kontejnerech klíčů najdete v tématu [Principy úrovni počítače a kontejnery klíčů RSA individuální](https://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9).</span><span class="sxs-lookup"><span data-stu-id="a9d50-105">For more information on key containers, see [Understanding Machine-Level and User-Level RSA Key Containers](https://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9).</span></span>  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="a9d50-106">K vytvoření asymetrický klíč a uložit ho v kontejneru klíčů</span><span class="sxs-lookup"><span data-stu-id="a9d50-106">To create an asymmetric key and save it in a key container</span></span>  
  
1.  <span data-ttu-id="a9d50-107">Vytvořit novou instanci třídy <xref:System.Security.Cryptography.CspParameters> třídy a předat název, který chcete volat kontejner klíčů <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> pole.</span><span class="sxs-lookup"><span data-stu-id="a9d50-107">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>  
  
2.  <span data-ttu-id="a9d50-108">Vytvořit novou instanci třídy, která je odvozena z <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy (obvykle **RSACryptoServiceProvider** nebo **DSACryptoServiceProvider**) a předejte mu dříve vytvořený  **CspParameters** objekt konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="a9d50-108">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
### <a name="to-delete-the-key-from-a-key-container"></a><span data-ttu-id="a9d50-109">K odstranění klíče z kontejneru klíčů</span><span class="sxs-lookup"><span data-stu-id="a9d50-109">To delete the key from a key container</span></span>  
  
1.  <span data-ttu-id="a9d50-110">Vytvořit novou instanci třídy **CspParameters** třídy a předat název, který chcete volat kontejner klíčů **CspParameters.KeyContainerName** pole.</span><span class="sxs-lookup"><span data-stu-id="a9d50-110">Create a new instance of a **CspParameters** class and pass the name that you want to call the key container to the **CspParameters.KeyContainerName** field.</span></span>  
  
2.  <span data-ttu-id="a9d50-111">Vytvořit novou instanci třídy, která je odvozena z **AsymmetricAlgorithm** třídy (obvykle **RSACryptoServiceProvider** nebo **DSACryptoServiceProvider**) a předat dříve vytvořili **CspParameters** objekt konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="a9d50-111">Create a new instance of a class that derives from the **AsymmetricAlgorithm** class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
3.  <span data-ttu-id="a9d50-112">Nastavte **PersistKeyInCSP** vlastnost, která je odvozena z třídy **AsymmetricAlgorithm** k **false** (**False** v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a9d50-112">Set the **PersistKeyInCSP** property of the class that derives from **AsymmetricAlgorithm** to **false** (**False** in Visual Basic).</span></span>  
  
4.  <span data-ttu-id="a9d50-113">Volání **vymazat** metoda, která je odvozena z třídy **AsymmetricAlgorithm**.</span><span class="sxs-lookup"><span data-stu-id="a9d50-113">Call the **Clear** method of the class that derives from **AsymmetricAlgorithm**.</span></span> <span data-ttu-id="a9d50-114">Tato metoda uvolní všechny prostředky třídy a vymaže kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="a9d50-114">This method releases all resources of the class and clears the key container.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9d50-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9d50-115">Example</span></span>  
 <span data-ttu-id="a9d50-116">Následující příklad ukazuje, jak vytvořit asymetrického klíče, uložte jej v kontejneru klíčů, později načíst klíč a odstranění klíče z kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a9d50-116">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>  
  
 <span data-ttu-id="a9d50-117">Všimněte si, že kód v `GenKey_SaveInContainer` metoda a `GetKeyFromContainer` metoda je podobná.</span><span class="sxs-lookup"><span data-stu-id="a9d50-117">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span>  <span data-ttu-id="a9d50-118">Pokud zadáte název kontejneru klíčů <xref:System.Security.Cryptography.CspParameters> objektu a předejte ji do <xref:System.Security.Cryptography.AsymmetricAlgorithm> objekt s <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> vlastnost nebo <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> vlastnost nastavena na hodnotu true, dojde k následujícímu.</span><span class="sxs-lookup"><span data-stu-id="a9d50-118">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to true, the following occurs.</span></span>  <span data-ttu-id="a9d50-119">Pokud kontejner klíče se zadaným názvem neexistuje, vytvoří a klíč je trvalá.</span><span class="sxs-lookup"><span data-stu-id="a9d50-119">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>  <span data-ttu-id="a9d50-120">Pokud kontejner klíče se zadaným názvem neexistuje, pak klíč v kontejneru je automaticky načten do aktuální <xref:System.Security.Cryptography.AsymmetricAlgorithm> objektu.</span><span class="sxs-lookup"><span data-stu-id="a9d50-120">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>  <span data-ttu-id="a9d50-121">Proto kód `GenKey_SaveInContainer` metoda uchovává klíč, protože se spouští jako první, zatímco kód v `GetKeyFromContainer` metoda načítá klíč, protože je spuštěn jako druhý.</span><span class="sxs-lookup"><span data-stu-id="a9d50-121">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it is run second.</span></span>  
  
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
  
```Output  
Key added to container:  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key retrieved from container :  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key deleted.  
Key added to container:  
<RSAKeyValue> Key Information B</RSAKeyValue>  
Key deleted.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9d50-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9d50-122">See also</span></span>

- [<span data-ttu-id="a9d50-123">Generování klíčů pro šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="a9d50-123">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
- [<span data-ttu-id="a9d50-124">Šifrování dat</span><span class="sxs-lookup"><span data-stu-id="a9d50-124">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)  
- [<span data-ttu-id="a9d50-125">Dešifrování dat</span><span class="sxs-lookup"><span data-stu-id="a9d50-125">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)  
- [<span data-ttu-id="a9d50-126">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="a9d50-126">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
