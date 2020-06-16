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
# <a name="store-asymmetric-keys-in-a-key-container"></a>Uložení asymetrických klíčů v kontejneru klíčů

Asymetrické soukromé klíče by nikdy neměly být uloženy doslovně nebo ve formátu prostého textu v místním počítači. Pokud potřebujete uložit privátní klíč, použijte kontejner klíčů. Další informace o kontejnerech klíčů najdete v tématu [Principy kontejnerů klíčů RSA na úrovni počítače a na úrovni uživatele](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).

## <a name="create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Vytvoření asymetrického klíče a jeho uložení do kontejneru klíčů

1. Vytvořte novou instanci <xref:System.Security.Cryptography.CspParameters> třídy a předejte název, který chcete zavolat kontejner klíčů do <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> pole.

1. Vytvořte novou instanci třídy, která je odvozena z <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy (obvykle <xref:System.Security.Cryptography.RSACryptoServiceProvider> nebo <xref:System.Security.Cryptography.DSACryptoServiceProvider> ) a předejte dříve vytvořený `CspParameters` objekt konstruktoru.

> [!NOTE]
> Vytvoření a načtení asymetrického klíče je jedna operace. Pokud klíč v kontejneru ještě není, vytvoří se před tím, než se vrátí.
>
> - <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType>
> - <xref:System.Security.Cryptography.DSA.ToXmlString%2A?displayProperty=nameWithType>

## <a name="delete-the-key-from-the-key-container"></a>Odstranit klíč z kontejneru klíčů

1. Vytvořte novou instanci `CspParameters` třídy a předejte název, který chcete zavolat kontejner klíčů do <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> pole.

1. Vytvořte novou instanci třídy, která je odvozena z <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy (obvykle `RSACryptoServiceProvider` nebo `DSACryptoServiceProvider` ) a předejte dříve vytvořený `CspParameters` objekt konstruktoru.

1. Nastavte <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> vlastnost nebo třídy, která je odvozena z `AsymmetricAlgorithm` na `false` ( `False` v Visual Basic).

1. Zavolejte `Clear` metodu třídy, která je odvozena z `AsymmetricAlgorithm` . Tato metoda uvolní všechny prostředky třídy a vymaže kontejner klíčů.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit asymetrický klíč, uložit ho do kontejneru klíčů, načíst klíč později a odstranit klíč z kontejneru.

Všimněte si, že kód v `GenKey_SaveInContainer` metodě a `GetKeyFromContainer` metodě je podobný. Když zadáte název kontejneru klíčů pro <xref:System.Security.Cryptography.CspParameters> objekt a předáte ho <xref:System.Security.Cryptography.AsymmetricAlgorithm> objektu s <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> vlastností nebo vlastností <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> nastavenou na `true` , chování je následující:

- Pokud kontejner klíčů se zadaným názvem neexistuje, vytvoří se a klíč se uloží.
- Pokud existuje kontejner klíčů se zadaným názvem, klíč v kontejneru se automaticky načte do aktuálního <xref:System.Security.Cryptography.AsymmetricAlgorithm> objektu.

Proto kód v `GenKey_SaveInContainer` metodě uchovává klíč, protože je spuštěn jako první, zatímco kód v `GetKeyFromContainer` metodě načte klíč, protože je spuštěn sekunda.

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

Výstup je následující:

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

## <a name="see-also"></a>Viz také

- [Generování klíčů pro šifrování a dešifrování](generating-keys-for-encryption-and-decryption.md)
- [Šifrování dat](encrypting-data.md)
- [Dešifrování dat](decrypting-data.md)
- [Kryptografické služby](cryptographic-services.md)
