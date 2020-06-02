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
ms.openlocfilehash: 246028566c59e5c8a77b26a21729d3f143d38d07
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289704"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a>Návod: Vytvoření šifrovací aplikace
Tento návod ukazuje, jak šifrovat a dešifrovat obsah. Příklady kódu jsou určeny pro model Windows Forms aplikace. Tato aplikace nemonstruje scénáře reálného světa, jako je například použití čipových karet. Místo toho ukazuje základy šifrování a dešifrování.  
  
 Tento návod používá pro šifrování následující pokyny:  
  
- Použijte <xref:System.Security.Cryptography.RijndaelManaged> třídu, symetrický algoritmus pro šifrování a dešifrování dat pomocí automatického vygenerovaného <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> a <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> .  
  
- Použijte <xref:System.Security.Cryptography.RSACryptoServiceProvider> asymetrický algoritmus pro šifrování a dešifrování klíče pro data zašifrovaná pomocí <xref:System.Security.Cryptography.RijndaelManaged> . Asymetrické algoritmy se nejlépe používají pro menší objemy dat, jako je například klíč.  
  
    > [!NOTE]
    > Chcete-li chránit data v počítači namísto výměny šifrovaného obsahu s jinými lidmi, zvažte použití <xref:System.Security.Cryptography.ProtectedData> <xref:System.Security.Cryptography.ProtectedMemory> tříd nebo.  
  
 Následující tabulka shrnuje kryptografické úlohy v tomto tématu.  
  
|Úkol|Popis|  
|----------|-----------------|  
|Vytvoření aplikace model Windows Forms|Seznam ovládacích prvků, které jsou požadovány ke spuštění aplikace.|  
|Deklarace globálních objektů|Deklaruje proměnné cesty k řetězci, <xref:System.Security.Cryptography.CspParameters> a a má <xref:System.Security.Cryptography.RSACryptoServiceProvider> globální kontext <xref:System.Windows.Forms.Form> třídy.|  
|Vytváření asymetrického klíče|Vytvoří asymetrickou dvojici hodnot veřejného a privátního klíče a přiřadí jí název kontejneru klíčů.|  
|Šifrování souboru|Zobrazí dialogové okno pro výběr souboru pro šifrování a zašifruje soubor.|  
|Dešifrování souboru|Zobrazí dialogové okno, ve kterém můžete vybrat zašifrovaný soubor pro dešifrování a dešifrovat soubor.|  
|Získání privátního klíče|Získá úplnou dvojici klíčů pomocí názvu kontejneru klíčů.|  
|Export veřejného klíče|Uloží klíč do souboru XML s pouze veřejnými parametry.|  
|Import veřejného klíče|Načte klíč ze souboru XML do kontejneru klíčů.|  
|Testování aplikace|Uvádí postupy pro testování této aplikace.|  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
- Odkazy na <xref:System.IO> <xref:System.Security.Cryptography> obory názvů a.  
  
## <a name="creating-a-windows-forms-application"></a>Vytvoření aplikace model Windows Forms  
 Většina příkladů kódu v tomto návodu je navržena jako obslužné rutiny událostí pro ovládací prvky tlačítek. V následující tabulce jsou uvedeny ovládací prvky požadované pro ukázkovou aplikaci a jejich požadované názvy, aby odpovídaly příkladům kódu.  
  
|Řízení|Name|Vlastnost text (podle potřeby)|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|Šifrovat soubor|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|Dešifrovat soubor|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|Vytvořit klíče|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|Exportovat veřejný klíč|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|Importovat veřejný klíč|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|Získat privátní klíč|  
|<xref:System.Windows.Forms.Label>|`label1`|Klíč není nastaven.|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 Dvojím kliknutím na tlačítka v návrháři sady Visual Studio vytvořte obslužné rutiny událostí.  
  
## <a name="declaring-global-objects"></a>Deklarace globálních objektů  
 Do konstruktoru formuláře přidejte následující kód. Upravte řetězcové proměnné pro vaše prostředí a předvolby.  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a>Vytváření asymetrického klíče  
 Tato úloha vytvoří asymetrický klíč, který šifruje a dešifruje <xref:System.Security.Cryptography.RijndaelManaged> klíč. Tento klíč se použil k zašifrování obsahu a zobrazuje název kontejneru klíčů v ovládacím prvku popisek.  
  
 Přidejte následující kód jako `Click` obslužnou rutinu události pro `Create Keys` tlačítko ( `buttonCreateAsmKeys_Click` ).  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a>Šifrování souboru  
 Tato úloha zahrnuje dvě metody: metodu obslužné rutiny události pro `Encrypt File` tlačítko ( `buttonEncryptFile_Click` ) a `EncryptFile` metodu. První metoda zobrazí dialogové okno pro výběr souboru a předá název souboru druhé metodě, která provádí šifrování.  
  
 Zašifrovaný obsah, klíč a IV jsou uloženy do jednoho <xref:System.IO.FileStream> , který je označován jako balíček šifrování.  
  
 `EncryptFile`Metoda provede následující akce:  
  
1. Vytvoří <xref:System.Security.Cryptography.RijndaelManaged> symetrický algoritmus pro šifrování obsahu.  
  
2. Vytvoří <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pro šifrování <xref:System.Security.Cryptography.RijndaelManaged> klíče.  
  
3. Používá <xref:System.Security.Cryptography.CryptoStream> objekt ke čtení a šifrování <xref:System.IO.FileStream> zdrojového souboru, v blocích bajtů, do cílového <xref:System.IO.FileStream> objektu pro zašifrovaný soubor.  
  
4. Určuje délku šifrovaného klíče a IV a vytvoří pole bajtů jejich hodnot délky.  
  
5. Zapíše klíč, IV a jejich hodnoty délky do šifrovaného balíčku.  
  
 Šifrovací balíček používá následující formát:  
  
- Délka klíče, bajty 0-3  
  
- Délka IV, bajty 4-7  
  
- Šifrovaný klíč  
  
- IV  
  
- Šifrovaný text  
  
 Délku klíče a IV můžete použít k určení počátečních bodů a délek všech částí šifrovacího balíčku, které pak můžete použít k dešifrování souboru.  
  
 Přidejte následující kód jako `Click` obslužnou rutinu události pro `Encrypt File` tlačítko ( `buttonEncryptFile_Click` ).  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 `EncryptFile`Do formuláře přidejte následující metodu.  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a>Dešifrování souboru  
 Tato úloha zahrnuje dvě metody, metodu obslužné rutiny události pro `Decrypt File` tlačítko ( `buttonDecryptFile_Click` ) a `DecryptFile` metodu. První metoda zobrazí dialogové okno pro výběr souboru a předá jeho název souboru druhé metodě, která provádí dešifrování.  
  
 `Decrypt`Metoda provede následující akce:  
  
1. Vytvoří <xref:System.Security.Cryptography.RijndaelManaged> symetrický algoritmus pro dešifrování obsahu.  
  
2. Přečte prvních osm bajtů <xref:System.IO.FileStream> zašifrovaného balíčku do polí bajtů, aby získala délky šifrovaného klíče a IV.  
  
3. Extrahuje klíč a IV z šifrovacího balíčku do polí bajtů.  
  
4. Vytvoří <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pro dešifrování <xref:System.Security.Cryptography.RijndaelManaged> klíče.  
  
5. Používá <xref:System.Security.Cryptography.CryptoStream> objekt pro čtení a dešifrování oddílu šifry textu <xref:System.IO.FileStream> v balíčku šifrování v blocích bajtů do <xref:System.IO.FileStream> objektu pro dešifrovaný soubor. Po dokončení se dešifrování dokončí.  
  
 Přidejte následující kód jako `Click` obslužnou rutinu události pro `Decrypt File` tlačítko.  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 `DecryptFile`Do formuláře přidejte následující metodu.  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a>Export veřejného klíče  
 Tento úkol uloží klíč vytvořený `Create Keys` tlačítkem do souboru. Exportuje pouze veřejné parametry.  
  
 Tato úloha simuluje scénář Alice, která dává Bobovi veřejný klíč, aby k nim mohl šifrovat soubory. A ostatní, kteří mají tento veřejný klíč, nebudou schopni je dešifrovat, protože nemají úplný pár klíčů s privátními parametry.  
  
 Přidejte následující kód jako `Click` obslužnou rutinu události pro `Export Public Key` tlačítko ( `buttonExportPublicKey_Click` ).  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a>Import veřejného klíče  
 Tato úloha načte klíč jenom s veřejnými parametry, jak je vytvořil `Export Public Key` tlačítko, a nastaví ho jako název kontejneru klíčů.  
  
 Tato úloha simuluje scénář, který Bob načítá klíč Alice, jenom s veřejnými parametry, aby k nim mohl šifrovat soubory.  
  
 Přidejte následující kód jako `Click` obslužnou rutinu události pro `Import Public Key` tlačítko ( `buttonImportPublicKey_Click` ).  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a>Získání privátního klíče  
 Tato úloha nastaví název kontejneru klíčů na název klíče vytvořeného pomocí `Create Keys` tlačítka. Kontejner klíčů bude obsahovat úplný pár klíčů s privátními parametry.  
  
 Tato úloha simuluje scénář Alice, který používá svůj privátní klíč k dešifrování souborů šifrovaných Bobem.  
  
 Přidejte následující kód jako `Click` obslužnou rutinu události pro `Get Private Key` tlačítko ( `buttonGetPrivateKey_Click` ).  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Po vytvoření aplikace proveďte následující testovací scénáře.  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a>Vytvoření klíčů, šifrování a dešifrování  
  
1. Klikněte na tlačítko `Create Keys`. Popisek zobrazí název klíče a ukáže, že se jedná o úplný pár klíčů.  
  
2. Klikněte na tlačítko `Export Public Key`. Všimněte si, že export parametrů veřejného klíče nemění aktuální klíč.  
  
3. Klikněte na `Encrypt File` tlačítko a vyberte soubor.  
  
4. Klikněte na `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný.  
  
5. Prověřte soubor, který se právě dešifroval.  
  
6. Zavřete aplikaci a restartujte ji, abyste v dalším scénáři otestovali načtení trvalých kontejnerů klíčů.  
  
#### <a name="to-encrypt-using-the-public-key"></a>Šifrování pomocí veřejného klíče  
  
1. Klikněte na tlačítko `Import Public Key`. Popisek zobrazí název klíče a ukáže, že je pouze veřejný.  
  
2. Klikněte na `Encrypt File` tlačítko a vyberte soubor.  
  
3. Klikněte na `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný. To se nezdaří, protože musíte mít privátní klíč k dešifrování.  
  
 Tento scénář ukazuje pouze veřejný klíč k šifrování souboru pro jinou osobu. Obvykle vám někdo poskytne jenom veřejný klíč a odpírá privátní klíč k dešifrování.  
  
#### <a name="to-decrypt-using-the-private-key"></a>Dešifrování pomocí privátního klíče  
  
1. Klikněte na tlačítko `Get Private Key`. Popisek zobrazí název klíče a ukáže, zda se jedná o úplný pár klíčů.  
  
2. Klikněte na `Decrypt File` tlačítko a vyberte soubor právě zašifrovaný. Tato akce bude úspěšná, protože máte úplný pár klíčů k dešifrování.  
  
## <a name="see-also"></a>Viz také

- [Kryptografické služby](cryptographic-services.md)
