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
ms.openlocfilehash: 3db4afb00367f719391193ebce4053cc5da16164
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588853"
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a>Postupy: Uložení asymetrického klíče v kontejneru klíčů
Asymetrické soukromé klíče by nikdy neměly být uloženy doslovně nebo ve formátu prostého textu v místním počítači. Pokud potřebujete uložit soukromý klíč, měli byste použít kontejner klíčů. Další informace o kontejnerech klíčů najdete v tématu [Principy úrovni počítače a kontejnery klíče RSA individuální](https://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9).  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a>Chcete vytvořit asymetrický klíč a uložit ho v kontejneru klíčů  
  
1.  Vytvořit novou instanci třídy <xref:System.Security.Cryptography.CspParameters> třídy a předat název, který chcete kontejner klíčů <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> pole.  
  
2.  Vytvořit novou instanci třídy odvozené z <xref:System.Security.Cryptography.AsymmetricAlgorithm> – třída (obvykle **RSACryptoServiceProvider** nebo **DSACryptoServiceProvider**) a předejte dříve vytvořenou  **CspParameters** objekt jeho konstruktoru.  
  
### <a name="to-delete-the-key-from-a-key-container"></a>K odstranění klíče z kontejneru klíčů  
  
1.  Vytvořit novou instanci třídy **CspParameters** třídy a předat název, který chcete kontejner klíčů **CspParameters.KeyContainerName** pole.  
  
2.  Vytvořit novou instanci třídy odvozené z **AsymmetricAlgorithm** – třída (obvykle **RSACryptoServiceProvider** nebo **DSACryptoServiceProvider**) a předat vytvořili **CspParameters** objekt jeho konstruktoru.  
  
3.  Nastavte **PersistKeyInCSP** vlastnost třídy, která je odvozena z **AsymmetricAlgorithm** k **false** (**False** v jazyce Visual Basic).  
  
4.  Volání **zrušte** metoda třídu odvozenou od **AsymmetricAlgorithm**. Tato metoda uvolní všechny prostředky třídy a vymaže kontejneru klíčů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit asymetrický klíč, uložit jej v kontejneru klíčů, načíst klíč později a odstranění klíče z kontejneru.  
  
 Všimněte si, že kód `GenKey_SaveInContainer` metoda a `GetKeyFromContainer` metoda je podobný.  Pokud zadáte název kontejneru klíčů <xref:System.Security.Cryptography.CspParameters> objektu a předejte jej <xref:System.Security.Cryptography.AsymmetricAlgorithm> objektu s <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> vlastnost nebo <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> vlastnost nastavena na hodnotu true a dojde k následujícímu.  Pokud kontejneru klíčů se zadaným názvem neexistuje, vytvoří se a klíč je trvalá.  Pokud kontejneru klíčů se zadaným názvem neexistuje, pak klíč v kontejneru je automaticky načtena do aktuální <xref:System.Security.Cryptography.AsymmetricAlgorithm> objektu.  Proto kód `GenKey_SaveInContainer` metoda uchovává klíč, protože je spuštěn jako první, zatímco kód v `GetKeyFromContainer` metoda načítá klíč, protože je spuštěn jako druhý.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [Šifrování dat](../../../docs/standard/security/encrypting-data.md)  
 [Dešifrování dat](../../../docs/standard/security/decrypting-data.md)  
 [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
