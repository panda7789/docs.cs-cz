---
title: 'Postupy: ukládání asymetrických klíčů v kontejneru klíčů'
description: Naučte se ukládat asymetrické klíče do kontejneru klíčů v .NET. Podívejte se, jak vytvořit asymetrický klíč, uložit ho do kontejneru klíčů a načíst a odstranit klíč.
ms.date: 05/26/2020
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
ms.openlocfilehash: a0fbde37491043cc1aab71e9733087bf410b997d
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769025"
---
# <a name="store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="3dd83-104">Uložení asymetrických klíčů v kontejneru klíčů</span><span class="sxs-lookup"><span data-stu-id="3dd83-104">Store asymmetric keys in a key container</span></span>

<span data-ttu-id="3dd83-105">Asymetrické soukromé klíče by nikdy neměly být uloženy doslovně nebo ve formátu prostého textu v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="3dd83-105">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="3dd83-106">Pokud potřebujete uložit privátní klíč, použijte kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="3dd83-106">If you need to store a private key, use a key container.</span></span> <span data-ttu-id="3dd83-107">Další informace o kontejnerech klíčů najdete v tématu [Principy kontejnerů klíčů RSA na úrovni počítače a na úrovni uživatele](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3dd83-107">For more information on key containers, see [Understanding machine-level and user-level RSA key containers](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span></span>

## <a name="create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="3dd83-108">Vytvoření asymetrického klíče a jeho uložení do kontejneru klíčů</span><span class="sxs-lookup"><span data-stu-id="3dd83-108">Create an asymmetric key and save it in a key container</span></span>

1. <span data-ttu-id="3dd83-109">Vytvořte novou instanci <xref:System.Security.Cryptography.CspParameters> třídy a předejte název, který chcete zavolat kontejner klíčů do <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> pole.</span><span class="sxs-lookup"><span data-stu-id="3dd83-109">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="3dd83-110">Vytvořte novou instanci třídy, která je odvozena z <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy (obvykle <xref:System.Security.Cryptography.RSACryptoServiceProvider> nebo <xref:System.Security.Cryptography.DSACryptoServiceProvider> ) a předejte dříve vytvořený `CspParameters` objekt konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="3dd83-110">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually <xref:System.Security.Cryptography.RSACryptoServiceProvider> or <xref:System.Security.Cryptography.DSACryptoServiceProvider>) and pass the previously created `CspParameters` object to its constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="3dd83-111">Vytvoření a načtení asymetrického klíče je jedna operace.</span><span class="sxs-lookup"><span data-stu-id="3dd83-111">The creation and retrieval of an asymmetric key is one operation.</span></span> <span data-ttu-id="3dd83-112">Pokud klíč v kontejneru ještě není, vytvoří se před tím, než se vrátí.</span><span class="sxs-lookup"><span data-stu-id="3dd83-112">If a key is not already in the container, it's created before being returned.</span></span>
>
> - <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType>
> - <xref:System.Security.Cryptography.DSA.ToXmlString%2A?displayProperty=nameWithType>

## <a name="delete-the-key-from-the-key-container"></a><span data-ttu-id="3dd83-113">Odstranit klíč z kontejneru klíčů</span><span class="sxs-lookup"><span data-stu-id="3dd83-113">Delete the key from the key container</span></span>

1. <span data-ttu-id="3dd83-114">Vytvořte novou instanci `CspParameters` třídy a předejte název, který chcete zavolat kontejner klíčů do <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> pole.</span><span class="sxs-lookup"><span data-stu-id="3dd83-114">Create a new instance of a `CspParameters` class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="3dd83-115">Vytvořte novou instanci třídy, která je odvozena z <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy (obvykle `RSACryptoServiceProvider` nebo `DSACryptoServiceProvider` ) a předejte dříve vytvořený `CspParameters` objekt konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="3dd83-115">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually `RSACryptoServiceProvider` or `DSACryptoServiceProvider`) and pass the previously created `CspParameters` object to its constructor.</span></span>

1. <span data-ttu-id="3dd83-116">Nastavte <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> vlastnost nebo třídy, která je odvozena z `AsymmetricAlgorithm` na `false` ( `False` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3dd83-116">Set the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> or the <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> property of the class that derives from `AsymmetricAlgorithm` to `false` (`False` in Visual Basic).</span></span>

1. <span data-ttu-id="3dd83-117">Zavolejte `Clear` metodu třídy, která je odvozena z `AsymmetricAlgorithm` .</span><span class="sxs-lookup"><span data-stu-id="3dd83-117">Call the `Clear` method of the class that derives from `AsymmetricAlgorithm`.</span></span> <span data-ttu-id="3dd83-118">Tato metoda uvolní všechny prostředky třídy a vymaže kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="3dd83-118">This method releases all resources of the class and clears the key container.</span></span>

## <a name="example"></a><span data-ttu-id="3dd83-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="3dd83-119">Example</span></span>

<span data-ttu-id="3dd83-120">Následující příklad ukazuje, jak vytvořit asymetrický klíč, uložit ho do kontejneru klíčů, načíst klíč později a odstranit klíč z kontejneru.</span><span class="sxs-lookup"><span data-stu-id="3dd83-120">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>

<span data-ttu-id="3dd83-121">Všimněte si, že kód v `GenKey_SaveInContainer` metodě a `GetKeyFromContainer` metodě je podobný.</span><span class="sxs-lookup"><span data-stu-id="3dd83-121">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span> <span data-ttu-id="3dd83-122">Když zadáte název kontejneru klíčů pro <xref:System.Security.Cryptography.CspParameters> objekt a předáte ho <xref:System.Security.Cryptography.AsymmetricAlgorithm> objektu s <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> vlastností nebo vlastností <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> nastavenou na `true` , chování je následující:</span><span class="sxs-lookup"><span data-stu-id="3dd83-122">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to `true`, the behavior is as follows:</span></span>

- <span data-ttu-id="3dd83-123">Pokud kontejner klíčů se zadaným názvem neexistuje, vytvoří se a klíč se uloží.</span><span class="sxs-lookup"><span data-stu-id="3dd83-123">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>
- <span data-ttu-id="3dd83-124">Pokud existuje kontejner klíčů se zadaným názvem, klíč v kontejneru se automaticky načte do aktuálního <xref:System.Security.Cryptography.AsymmetricAlgorithm> objektu.</span><span class="sxs-lookup"><span data-stu-id="3dd83-124">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>

<span data-ttu-id="3dd83-125">Proto kód v `GenKey_SaveInContainer` metodě uchovává klíč, protože je spuštěn jako první, zatímco kód v `GetKeyFromContainer` metodě načte klíč, protože je spuštěn sekunda.</span><span class="sxs-lookup"><span data-stu-id="3dd83-125">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it's run second.</span></span>

```vb
Imports System
Imports System.Security.Cryptography

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

    Private Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        ' name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key added to container:  {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub GetKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key retrieved from container : {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container.
        ' Delete the key entry in the container.
        Dim rsa As New RSACryptoServiceProvider(parameters) With {
            .PersistKeyInCsp = False
        }

        ' Call Clear to release resources and delete the key from the container.
        rsa.Clear()

        Console.WriteLine("Key deleted.")
    End Sub
End Class
```

```csharp
using System;
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
        catch (CryptographicException e)
        {
            Console.WriteLine(e.Message);
        }
    }

    private static void GenKey_SaveInContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key added to container: \n  {rsa.ToXmlString(true)}");
    }

    private static void GetKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key retrieved from container : \n {rsa.ToXmlString(true)}");
    }

    private static void DeleteKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container.
        using var rsa = new RSACryptoServiceProvider(parameters)
        {
            // Delete the key entry in the container.
            PersistKeyInCsp = false
        };

        // Call Clear to release resources and delete the key from the container.
        rsa.Clear();

        Console.WriteLine("Key deleted.");
    }
}
```

<span data-ttu-id="3dd83-126">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="3dd83-126">The output is as follows:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3dd83-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dd83-127">See also</span></span>

- [<span data-ttu-id="3dd83-128">Generování klíčů pro šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="3dd83-128">Generating keys for encryption and decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="3dd83-129">Šifrování dat</span><span class="sxs-lookup"><span data-stu-id="3dd83-129">Encrypting data</span></span>](encrypting-data.md)
- [<span data-ttu-id="3dd83-130">Dešifrování dat</span><span class="sxs-lookup"><span data-stu-id="3dd83-130">Decrypting data</span></span>](decrypting-data.md)
- [<span data-ttu-id="3dd83-131">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="3dd83-131">Cryptographic services</span></span>](cryptographic-services.md)
