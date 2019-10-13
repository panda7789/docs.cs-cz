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
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a>Postupy: ukládání asymetrických klíčů v kontejneru klíčů
Asymetrické privátní klíče by nikdy neměly být uložené v místním počítači do doslovného znění ani do prostého textu. Pokud potřebujete uložit privátní klíč, měli byste použít kontejner klíčů. Další informace o kontejnerech klíčů najdete v tématu [Principy kontejnerů klíčů RSA na úrovni počítače a na úrovni uživatele](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Vytvoření asymetrického klíče a jeho uložení do kontejneru klíčů  
  
1. Vytvořte novou instanci třídy <xref:System.Security.Cryptography.CspParameters> a předejte název, který chcete volat kontejner klíčů, do pole <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType>.  
  
2. Vytvořte novou instanci třídy, která je odvozena z třídy <xref:System.Security.Cryptography.AsymmetricAlgorithm> (obvykle **RSACryptoServiceProvider** nebo **DSACryptoServiceProvider**) a předejte dříve vytvořený objekt **CspParameters** konstruktoru.  
  
### <a name="to-delete-the-key-from-a-key-container"></a>Odstranění klíče z kontejneru klíčů  
  
1. Vytvořte novou instanci třídy **CspParameters** a předejte název, který chcete zavolat kontejneru klíčů do pole **CspParameters. ContainerName** .  
  
2. Vytvoří novou instanci třídy, která je odvozena z třídy **AsymmetricAlgorithm** (obvykle **RSACryptoServiceProvider** nebo **DSACryptoServiceProvider**) a předá dříve vytvořený objekt **CspParameters** do konstruktoru. .  
  
3. Nastavte vlastnost **PersistKeyInCsp** třídy, která je odvozena z **AsymmetricAlgorithm** na **false** (**false** v Visual Basic).  
  
4. Zavolejte metodu **clear** třídy, která je odvozena z **AsymmetricAlgorithm**. Tato metoda uvolní všechny prostředky třídy a vymaže kontejner klíčů.  
  
## <a name="example"></a>Příklad:  
 Následující příklad ukazuje, jak vytvořit asymetrický klíč, uložit ho do kontejneru klíčů, načíst klíč později a odstranit klíč z kontejneru.  
  
 Všimněte si, že kód v metodě `GenKey_SaveInContainer` a v metodě `GetKeyFromContainer` je podobný.  Když zadáte název kontejneru klíčů pro objekt @no__t 0 a předáte ho do objektu <xref:System.Security.Cryptography.AsymmetricAlgorithm> s vlastností <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> nebo vlastností <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> nastavenou na hodnotu true, dojde k následujícímu:  Pokud kontejner klíčů se zadaným názvem neexistuje, vytvoří se a klíč se uloží.  Pokud existuje kontejner klíčů se zadaným názvem, klíč v kontejneru se automaticky načte do aktuálního objektu <xref:System.Security.Cryptography.AsymmetricAlgorithm>.  Proto kód v metodě `GenKey_SaveInContainer` uchovává klíč, protože je spuštěn jako první, zatímco kód v metodě `GetKeyFromContainer` načte klíč, protože se spustí sekunda.  
  
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
  
## <a name="see-also"></a>Další informace najdete v tématech

- [Generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [Šifrování dat](../../../docs/standard/security/encrypting-data.md)
- [Dešifrování dat](../../../docs/standard/security/decrypting-data.md)
- [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
