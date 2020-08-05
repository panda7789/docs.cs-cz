---
title: Šifrování dat
description: Naučte se šifrovat data v .NET pomocí symetrického algoritmu nebo asymetrického algoritmu.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], symmetric
- symmetric encryption
- cryptography [.NET], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 8a8b5988a13ab571284b08c7aaece3542467aa71
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556966"
---
# <a name="encrypting-data"></a>Šifrování dat

Symetrické šifrování a asymetrické šifrování se provádí pomocí různých procesů. Symetrické šifrování se provádí na datových proudech a je proto užitečné pro šifrování velkých objemů dat. Asymetrické šifrování se provádí na malém počtu bajtů a je proto užitečné jenom pro malé objemy dat.  
  
## <a name="symmetric-encryption"></a>Symetrické šifrování  

Spravované třídy symetrického kryptografie se používají se speciální třídou streamu nazvanou a <xref:System.Security.Cryptography.CryptoStream> , která šifruje data čtená do datového proudu. Třída **CryptoStream** je inicializována se třídou spravovaného datového proudu, třídou, která implementuje <xref:System.Security.Cryptography.ICryptoTransform> rozhraní (vytvořené z třídy, která implementuje kryptografický algoritmus), a <xref:System.Security.Cryptography.CryptoStreamMode> výčtem, který popisuje typ přístupu povoleného pro třídu **CryptoStream**. Třídu **CryptoStream** lze inicializovat pomocí libovolné třídy, která je odvozena od <xref:System.IO.Stream> třídy, včetně <xref:System.IO.FileStream> , <xref:System.IO.MemoryStream> a <xref:System.Net.Sockets.NetworkStream> . Pomocí těchto tříd můžete provádět symetrické šifrování u nejrůznějších objektů streamu.  
  
Následující příklad ukazuje, jak vytvořit novou instanci výchozí třídy implementace pro <xref:System.Security.Cryptography.Aes> algoritmus. Instance se používá k šifrování u třídy **CryptoStream** . V tomto příkladu je objekt **CryptoStream** inicializován pomocí objektu datového proudu s názvem `myStream` , který může být jakýkoli typ spravovaného datového proudu. Metodě **CreateEncryptor** z třídy **AES** je předán klíč a IV, který se používá k šifrování. V takovém případě se použije výchozí klíč a hodnota IV vygenerované z `aes` .
  
```vb  
Dim aes As Aes = Aes.Create()  
Dim cryptStream As New CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
```  
  
```csharp  
Aes aes = Aes.Create();  
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write);  
```  
  
Po spuštění tohoto kódu se všechna data zapsaná do objektu **CryptoStream** šifrují pomocí algoritmu AES.  
  
Následující příklad ukazuje celý proces vytvoření datového proudu, šifrování datového proudu, zápis do datového proudu a zavření datového proudu. Tento příklad vytvoří datový proud souboru, který je zašifrovaný pomocí třídy **CryptoStream** a třídy **AES** . Do šifrovaného datového proudu s třídou se zapisuje zpráva <xref:System.IO.StreamWriter> .
  
:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb":::

Kód šifruje datový proud pomocí symetrického algoritmu AES a zapisuje "Hello World!" do datového proudu. Pokud je kód úspěšný, vytvoří zašifrovaný soubor s názvem *TestData.txt* a zobrazí následující text v konzole:  
  
```console  
The text was encrypted.  
```  

Soubor můžete dešifrovat pomocí příkladu symetrického dešifrování při [dešifrování dat](decrypting-data.md). Tento příklad a v tomto příkladu určují stejný klíč a IV.

Nicméně pokud je vyvolána výjimka, kód zobrazí následující text konzole:  
  
```console  
The encryption failed.  
```

## <a name="asymmetric-encryption"></a>Asymetrické šifrování

Asymetrické algoritmy jsou obvykle používány k šifrování malých objemů dat, jako je například šifrování symetrického klíče a IV. Obvykle jednotlivec provádějící asymetrické šifrování používá veřejný klíč generovaný jinou stranou. <xref:System.Security.Cryptography.RSA>Třída je poskytována rozhraním .NET pro tento účel.  
  
Následující příklad používá informace o veřejném klíči k šifrování symetrického klíče a IV. Jsou inicializována dvě Bajtová pole, která představují veřejný klíč třetí strany. <xref:System.Security.Cryptography.RSAParameters>Objekt je inicializován na tyto hodnoty. Dále je objekt **RSAParameters** (spolu s veřejným klíčem, který představuje) importován do instance **RSA** pomocí <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> metody. Nakonec se šifrují privátní klíč a IV vytvořené <xref:System.Security.Cryptography.Aes> třídou. V tomto příkladu je potřeba, aby systémy měly nainstalované 128 bitového šifrování.  
  
```vb  
Imports System
Imports System.Security.Cryptography

Module Module1

    Sub Main()
        'Initialize the byte arrays to the public key information.  
        Dim modulus As Byte() = {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19, 202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}

        Dim exponent As Byte() = {1, 0, 1}

        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte
        Dim encryptedSymmetricIV() As Byte

        'Create a new instance of the default RSA implementation class.
        Dim rsa As RSA = RSA.Create()

        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()

        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus
        rsaKeyInfo.Exponent = exponent

        'Import key parameters into rsa
        rsa.ImportParameters(rsaKeyInfo)

        'Create a new instance of the default Aes implementation class.  
        Dim aes As Aes = Aes.Create()

        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1)
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1)
    End Sub

End Module
```  
  
```csharp  
using System;
using System.Security.Cryptography;

class Class1
{
    static void Main()
    {
        //Initialize the byte arrays to the public key information.  
        byte[] modulus = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};

        byte[] exponent = { 1, 0, 1 };

        //Create values to store encrypted symmetric keys.  
        byte[] encryptedSymmetricKey;
        byte[] encryptedSymmetricIV;

        //Create a new instance of the RSA class.  
        RSA rsa = RSA.Create();

        //Create a new instance of the RSAParameters structure.  
        RSAParameters rsaKeyInfo = new RSAParameters();

        //Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus;
        rsaKeyInfo.Exponent = exponent;

        //Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo);

        //Create a new instance of the default Aes implementation class.  
        Aes aes = Aes.Create();

        //Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1);
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1);
    }
}
```  
  
## <a name="see-also"></a>Viz také

- [Generování klíčů pro šifrování a dešifrování](generating-keys-for-encryption-and-decryption.md)
- [Dešifrování dat](decrypting-data.md)
- [Šifrovací služby](cryptographic-services.md)
- [Kryptografie pro různé platformy](cross-platform-cryptography.md)
- [Ohrožení zabezpečení časování u symetrického dešifrování pomocí odsazení v režimu CBC](vulnerabilities-cbc-mode.md)
- [Ochrana dat ASP.NET Core](/aspnet/core/security/data-protection/introduction)
