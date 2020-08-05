---
title: Dešifrování dat
description: Naučte se, jak dešifrovat data v .NET pomocí symetrického algoritmu nebo asymetrického algoritmu.
ms.date: 07/16/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: 2ba4c3ba43d688aeb66c67ec3f94f4a503d47892
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556979"
---
# <a name="decrypting-data"></a>Dešifrování dat

Dešifrování je reverzní operace šifrování. U šifrování tajného klíče je nutné znát klíč i IV, které byly použity k zašifrování dat. U šifrování veřejného klíče je nutné znát buď veřejný klíč (Pokud byla data zašifrovaná pomocí privátního klíče), nebo privátní klíč (Pokud byla data zašifrovaná pomocí veřejného klíče).

## <a name="symmetric-decryption"></a>Symetrické dešifrování

Dešifrování dat šifrovaných pomocí symetrických algoritmů je podobné procesu použitému k šifrování dat pomocí symetrických algoritmů. <xref:System.Security.Cryptography.CryptoStream>Třída se používá spolu se symetrickými třídami kryptografie poskytovanými rozhraním .NET k dešifrování dat přečtených z libovolného spravovaného objektu streamu.

Následující příklad ukazuje, jak vytvořit novou instanci výchozí třídy implementace pro <xref:System.Security.Cryptography.Aes> algoritmus. Instance se používá k dešifrování <xref:System.Security.Cryptography.CryptoStream> objektu. Tento příklad nejprve vytvoří novou instanci třídy implementace **AES** . Dále vytvoří objekt **CryptoStream** a inicializuje jej na hodnotu spravovaného datového proudu `myStream` . Dále metoda **CreateDecryptor** z třídy **AES** předává stejný klíč a IV, který byl použit pro šifrování a je pak předán konstruktoru **CryptoStream** .

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

Následující příklad ukazuje celý proces vytvoření datového proudu, dešifrování datového proudu, čtení z datového proudu a zavření datových proudů. Vytvoří se objekt datového proudu souboru, který přečte soubor s názvem *TestData.txt*. Datový proud souboru je poté dešifrován pomocí třídy **CryptoStream** a třídy **AES** . Tento příklad určuje klíče a hodnoty IV, které se používají v příkladu symetrického šifrování pro [šifrování dat](encrypting-data.md). Nezobrazuje kód potřebný k šifrování a přenos těchto hodnot.

```vb
Imports System
Imports System.IO
Imports System.Security.Cryptography

Module Module1
    Sub Main()
            'The key and IV must be the same values that were used
            'to encrypt the stream.
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
        Try
            'Create a file stream.
            Dim myStream As FileStream = new FileStream("TestData.txt", FileMode.Open)

            'Create a new instance of the default Aes implementation class
            'and decrypt the stream.
            Dim aes As Aes = Aes.Create()

            'Create an instance of the CryptoStream class, pass it the file stream, and decrypt
            'it with the Rijndael class using the key and IV.
            Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)

            'Read the stream.
            Dim sReader As New StreamReader(cryptStream)

            'Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd())

            'Close the streams.
            sReader.Close()
            myStream.Close()
            'Catch any exceptions.
        Catch
            Console.WriteLine("The decryption Failed.")
            Throw
        End Try
    End Sub
End Module
```

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

class Class1
{
    static void Main(string[] args)
    {
        //The key and IV must be the same values that were used
        //to encrypt the stream.
        byte[] key = { 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16 };
        byte[] iv = { 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16 };
        try
        {
            //Create a file stream.
            FileStream myStream = new FileStream("TestData.txt", FileMode.Open);

            //Create a new instance of the default Aes implementation class
            Aes aes = Aes.Create();

            //Create a CryptoStream, pass it the file stream, and decrypt
            //it with the Aes class using the key and IV.
            CryptoStream cryptStream = new CryptoStream(
               myStream,
               aes.CreateDecryptor(key, iv),
               CryptoStreamMode.Read);

            //Read the stream.
            StreamReader sReader = new StreamReader(cryptStream);

            //Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd());

            //Close the streams.
            sReader.Close();
            myStream.Close();
        }
        //Catch any exceptions.
        catch
        {
            Console.WriteLine("The decryption failed.");
            throw;
        }
    }
}
```

V předchozím příkladu se používá stejný klíč, IV a algoritmus, který se používá v příkladu symetrického šifrování pro [šifrování dat](encrypting-data.md). Dešifruje soubor *TestData.txt* , který je vytvořen tímto příkladem, a zobrazí původní text v konzole nástroje.

## <a name="asymmetric-decryption"></a>Asymetrické dešifrování

Strana (strana A) obvykle generuje veřejný i privátní klíč a ukládá klíč buď do paměti, nebo do kontejneru kryptografických klíčů. Strana A pak pošle veřejný klíč druhé straně (smluvní straně B). Když strana B použije veřejný klíč, zašifruje data a pošle je zpátky do strany A. Po přijetí dat ji strana dešifruje pomocí privátního klíče, který odpovídá. Dešifrování bude úspěšné pouze v případě, že strana A používá privátní klíč, který odpovídá veřejnému klíči B, který se používá k šifrování dat.

Informace o tom, jak uložit asymetrický klíč do kontejneru zabezpečeného kryptografického klíče a jak později získat asymetrický klíč, najdete v tématu [Postupy: ukládání asymetrických klíčů v kontejneru klíčů](how-to-store-asymmetric-keys-in-a-key-container.md).

Následující příklad znázorňuje dešifrování dvou polí bajtů, které reprezentují symetrický klíč a IV. Informace o tom, jak extrahovat asymetrický veřejný klíč z <xref:System.Security.Cryptography.RSA> objektu ve formátu, který lze snadno odeslat třetí straně, najdete v tématu [šifrování dat](encrypting-data.md).

```vb
'Create a new instance of the RSA class.
Dim rsa As RSA = RSA.Create()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, RSAEncryptionPadding.Pkcs1)
```

```csharp
//Create a new instance of the RSA class.
RSA rsa = RSA.Create();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , RSAEncryptionPadding.Pkcs1);
```

## <a name="see-also"></a>Viz také

- [Generování klíčů pro šifrování a dešifrování](generating-keys-for-encryption-and-decryption.md)
- [Šifrování dat](encrypting-data.md)
- [Šifrovací služby](cryptographic-services.md)
- [Kryptografický model](cryptography-model.md)
- [Kryptografie pro různé platformy](cross-platform-cryptography.md)
- [Ohrožení zabezpečení časování u symetrického dešifrování pomocí odsazení v režimu CBC](vulnerabilities-cbc-mode.md)
- [Ochrana dat ASP.NET Core](/aspnet/core/security/data-protection/introduction)
