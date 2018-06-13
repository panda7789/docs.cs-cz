---
title: 'Návod: Vytvoření šifrovací aplikace'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77debed932b78ae0aa1d8eebf54bd2d3bfbfea7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591960"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a>Návod: Vytvoření šifrovací aplikace
Tento návod ukazuje, jak k šifrování a dešifrování obsahu. Ukázky kódu jsou navrženy pro aplikace Windows Forms. Tuto aplikaci nepředvádí skutečných scénářích, například pomocí čipové karty. Místo toho ukazuje základní informace o šifrování a dešifrování.  
  
 Tento návod používá pro šifrování následující pokyny:  
  
-   Použití <xref:System.Security.Cryptography.RijndaelManaged> třídy symetrický algoritmus, k šifrování a dešifrování dat pomocí jeho automaticky generované <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> a <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.  
  
-   Použití <xref:System.Security.Cryptography.RSACryptoServiceProvider>, asymetrického algoritmu, k šifrování a dešifrování klíče, který se data zašifrovaná pomocí <xref:System.Security.Cryptography.RijndaelManaged>. Asymetrické algoritmy jsou nejvhodnější pro menší množství dat, jako jsou klíče.  
  
    > [!NOTE]
    >  Pokud chcete chránit data ve vašem počítači místo výměny šifrovaný obsah s jinými uživateli, zvažte použití <xref:System.Security.Cryptography.ProtectedData> nebo <xref:System.Security.Cryptography.ProtectedMemory> třídy.  
  
 Následující tabulka shrnuje kryptografické úlohy v tomto tématu.  
  
|Úloha|Popis|  
|----------|-----------------|  
|Vytvoření aplikace pro Windows Forms|Uvádí ovládacích prvků, které jsou nutné ke spuštění aplikace.|  
|Deklarování globální objekty|Deklaruje řetězec proměnné cest, <xref:System.Security.Cryptography.CspParameters>a <xref:System.Security.Cryptography.RSACryptoServiceProvider> tak, aby měl globální kontextu <xref:System.Windows.Forms.Form> třídy.|  
|Vytváření asymetrického klíče|Vytvoří dvojici asymetrické veřejné a soukromé klíče hodnotu a přiřadí ji název kontejneru klíčů.|  
|Šifrování souboru|Zobrazí dialogové okno a vyberte soubor pro šifrování a zašifrování souboru.|  
|Dešifrování souboru|Zobrazí dialogové okno vybrat zašifrovaný soubor pro dešifrování a soubor dešifruje.|  
|Získání privátního klíče|Získá úplný pár klíče pomocí názvu kontejneru klíčů.|  
|Export veřejného klíče|Uloží klíč do souboru XML s pouze veřejné parametry.|  
|Import veřejného klíče|Načte klíče ze souboru XML do kontejneru klíčů.|  
|Testování aplikace|Uvádí postupy pro testování této aplikace.|  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Odkazuje na <xref:System.IO> a <xref:System.Security.Cryptography> obory názvů.  
  
## <a name="creating-a-windows-forms-application"></a>Vytvoření aplikace Windows Forms  
 Většina příklady kódu v tomto průvodci jsou navržené jako obslužné rutiny události pro ovládací prvky tlačítek. Následující tabulka uvádí prvky, které jsou vyžadovány pro ukázkovou aplikaci a jejich požadované názvy tak, aby odpovídaly příklady kódu.  
  
|Ovládací prvek|Název|Text – vlastnost (podle potřeby)|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|Šifrování souborů|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|Dešifrování souboru|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|Vytvoření klíčů|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|Export veřejného klíče|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|Import veřejného klíče|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|Získání privátního klíče|  
|<xref:System.Windows.Forms.Label>|`label1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 Dvakrát klikněte na tlačítka v návrháři Visual Studio k vytvoření jejich obslužných rutin událostí.  
  
## <a name="declaring-global-objects"></a>Deklarování globální objekty  
 Přidejte následující kód do konstruktoru formuláře. Upravte proměnné řetězce pro vaše prostředí a předvolbám.  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a>Vytváření asymetrického klíče  
 Tato úloha vytvoří asymetrický klíč, který šifruje a dešifruje <xref:System.Security.Cryptography.RijndaelManaged> klíč. Tento klíč se používá k šifrování obsahu a zobrazí se název kontejneru klíčů na ovládací prvek popisek.  
  
 Přidejte následující kód, jako `Click` obslužné rutiny události pro `Create Keys` tlačítko (`buttonCreateAsmKeys_Click`).  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a>Šifrování souboru  
 Tato úloha zahrnuje dvě metody: metodu obslužné rutiny události pro `Encrypt File` tlačítko (`buttonEncryptFile_Click`) a `EncryptFile` metoda. První metoda zobrazí dialogové okno pro výběr souboru a předá název souboru do druhé metody, které provádí šifrování.  
  
 Šifrovaný obsah, klíče a IV všechna uložena do jednoho <xref:System.IO.FileStream>, což se označuje jako balíčku šifrování.  
  
 `EncryptFile` Metoda provede následující akce:  
  
1.  Vytvoří <xref:System.Security.Cryptography.RijndaelManaged> algoritmus symetrického šifrování obsahu.  
  
2.  Vytvoří <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt, který chcete zašifrovat <xref:System.Security.Cryptography.RijndaelManaged> klíč.  
  
3.  Používá <xref:System.Security.Cryptography.CryptoStream> objekt ke čtení a šifrování <xref:System.IO.FileStream> zdrojového souboru v blocích bajtů do cílového <xref:System.IO.FileStream> objekt pro šifrovaný soubor.  
  
4.  Určuje délky zašifrovaný klíč a IV a vytvoří jejich hodnoty pro délku pole bajtů.  
  
5.  Zapíše klíč, IV a jejich hodnoty pro délku do šifrovaného balíčku.  
  
 Balíček šifrování používá následující formát:  
  
-   Délka klíče, bajtů 0 - 3  
  
-   Délka IV, bajty 4-7  
  
-   Šifrovaný klíč  
  
-   IV  
  
-   Šifrovaný text  
  
 Délky klíče a IV můžete použít k určení počátečních bodů a délek všech částí šifrování balíčku, který můžete použít pro dešifrování souboru.  
  
 Přidejte následující kód, jako `Click` obslužné rutiny události pro `Encrypt File` tlačítko (`buttonEncryptFile_Click`).  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 Přidejte následující `EncryptFile` metoda do formuláře.  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a>Dešifrování souboru  
 Tato úloha zahrnuje dvě metody, metodu obslužné rutiny události pro `Decrypt File` tlačítko (`buttonEncryptFile_Click`) a `DecryptFile` metoda. První metoda zobrazí dialogové okno pro výběr souboru a předá její název souboru do druhé metody, která provádí dešifrování.  
  
 `Decrypt` Metoda provede následující akce:  
  
1.  Vytvoří <xref:System.Security.Cryptography.RijndaelManaged> symetrický algoritmus k dešifrování obsahu.  
  
2.  Přečte první osm bajtů <xref:System.IO.FileStream> šifrovaného balíčku do pole bajtů k získání délky zašifrovaný klíč a IV.  
  
3.  Extrahuje klíče a IV z balíčku šifrování do pole bajtů.  
  
4.  Vytvoří <xref:System.Security.Cryptography.RSACryptoServiceProvider> objektu k dešifrování <xref:System.Security.Cryptography.RijndaelManaged> klíč.  
  
5.  Používá <xref:System.Security.Cryptography.CryptoStream> objekt ke čtení a dešifrování části textu šifrovací <xref:System.IO.FileStream> šifrování balíčku, v blocích bajtů do <xref:System.IO.FileStream> objekt pro dešifrovaný soubor. Po jejím dokončení, dešifrování je dokončeno.  
  
 Přidejte následující kód, jako `Click` obslužné rutiny události pro `Decrypt File` tlačítko.  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 Přidejte následující `DecryptFile` metoda do formuláře.  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a>Export veřejného klíče  
 Tato úloha uloží klíč vytvořený `Create Keys` tlačítko do souboru. Exportuje pouze veřejné parametry.  
  
 Tato úloha simuluje scénář Alice poskytnutí Bob svůj veřejný klíč, aby mohl šifrovat soubory pro ní. On a ostatní používající tento veřejný klíč, nebudou moci dešifrovat, protože nemají úplný pár klíče s privátní parametry.  
  
 Přidejte následující kód, jako `Click` obslužné rutiny události pro `Export Public Key` tlačítko (`buttonExportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a>Import veřejného klíče  
 Tato úloha načte klíč s pouze veřejné parametry, jak je vytvořený `Export Public Key` tlačítko a nastaví jej jako název kontejneru klíče.  
  
 Tato úloha simuluje scénář Bob načítání klíče Alice s pouze veřejné parametry, tak pro ní může šifrovat soubory.  
  
 Přidejte následující kód, jako `Click` obslužné rutiny události pro `Import Public Key` tlačítko (`buttonImportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a>Získávání privátní klíč  
 Tato úloha nastaví název kontejneru klíče k názvu klíče vytvořeného pomocí `Create Keys` tlačítko. Kontejner klíče bude obsahovat úplný pár klíče s privátní parametry.  
  
 Tato úloha simuluje scénář, jak pomocí vlastního soukromého klíče k dešifrování souborů zašifrované Bob Alice.  
  
 Přidejte následující kód, jako `Click` obslužné rutiny události pro `Get Private Key` tlačítko (`buttonGetPrivateKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Po vytvoření aplikace, proveďte následující scénáře testování.  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a>K vytvoření klíčů, šifrování a dešifrování  
  
1.  Klikněte `Create Keys` tlačítko. Popisek zobrazí název klíče a ukazuje, že je to úplný pár klíče.  
  
2.  Klikněte `Export Public Key` tlačítko. Všimněte si, že export parametrů veřejného klíče nezmění aktuální klíč.  
  
3.  Klikněte `Encrypt File` tlačítko a vyberte soubor.  
  
4.  Klikněte `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.  
  
5.  Zkontrolujte v souboru právě dešifrovat.  
  
6.  Zavřete aplikaci a restartujte ji k otestování načítání trvalých kontejnerů klíčů v dalším scénáři.  
  
#### <a name="to-encrypt-using-the-public-key"></a>K šifrování pomocí veřejného klíče  
  
1.  Klikněte `Import Public Key` tlačítko. Popisek zobrazí název klíče a ukazuje, že je veřejný pouze.  
  
2.  Klikněte `Encrypt File` tlačítko a vyberte soubor.  
  
3.  Klikněte `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný. To se nezdaří, protože musí mít privátní klíč pro dešifrování.  
  
 Tento scénář ukazuje, jak máme pouze veřejný klíč k šifrování souboru pro jinou osobou. Obvykle je tato osoba by získáte pouze veřejný klíč a odepřela soukromý klíč pro dešifrování.  
  
#### <a name="to-decrypt-using-the-private-key"></a>Chcete-li dešifrovat pomocí soukromého klíče  
  
1.  Klikněte `Get Private Key` tlačítko. Popisek zobrazí název klíče a ukazuje, zda se jedná o úplný pár klíče.  
  
2.  Klikněte `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný. Tato funkce bude úspěšné, protože máte úplný pár klíče k dešifrování.  
  
## <a name="see-also"></a>Viz také  
 [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
