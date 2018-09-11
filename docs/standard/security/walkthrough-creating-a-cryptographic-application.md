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
ms.openlocfilehash: 873b6120929c8c7cf67d53d8f793964361ae88b8
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44337743"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a>Návod: Vytvoření šifrovací aplikace
Tento návod ukazuje, jak šifrování a dešifrování obsahu. Příklady kódu jsou určeny pro aplikaci Windows Forms. Tato aplikace neukazuje reálných scénářů, jako je například používání čipových karet. Místo toho ukazuje základní informace o šifrování a dešifrování.  
  
 Tento návod používá k šifrování podle následujících pokynů:  
  
-   Použití <xref:System.Security.Cryptography.RijndaelManaged> symetrický algoritmus pro šifrování a dešifrování dat pomocí jeho automaticky generované třídy <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> a <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.  
  
-   Použití <xref:System.Security.Cryptography.RSACryptoServiceProvider>, asymetrického algoritmu, k šifrování a dešifrování klíče k data zašifrovaná pomocí <xref:System.Security.Cryptography.RijndaelManaged>. Asymetrické algoritmy jsou nejvhodnější pro menší množství dat, jako jsou klíče.  
  
    > [!NOTE]
    >  Pokud chcete chránit data ve vašem počítači místo výměny šifrovaný obsah s jinými uživateli, zvažte použití <xref:System.Security.Cryptography.ProtectedData> nebo <xref:System.Security.Cryptography.ProtectedMemory> třídy.  
  
 Následující tabulka shrnuje šifrovací úlohy v tomto tématu.  
  
|Úloha|Popis|  
|----------|-----------------|  
|Vytvoření aplikace Windows Forms|Obsahuje ovládací prvky, které jsou potřeba ke spouštění aplikace.|  
|Deklarace globálních objektů|Deklaruje řetězec proměnné cesty <xref:System.Security.Cryptography.CspParameters>a <xref:System.Security.Cryptography.RSACryptoServiceProvider> mít globální kontext <xref:System.Windows.Forms.Form> třídy.|  
|Vytváření asymetrický klíč|Vytvoří pár asymetrických veřejného a privátního klíče hodnotu a přiřadí ji název kontejneru klíčů.|  
|Šifrování souboru|Zobrazí dialogové okno pro výběr souboru pro šifrování a zašifruje souboru.|  
|Dešifrování souboru|Zobrazí dialogové okno vybrat zašifrovaný soubor pro dešifrování a dešifruje soubor.|  
|Získání privátní klíč|Získá úplný pár klíče pomocí názvu kontejneru klíčů.|  
|Export veřejného klíče|Uloží klíč do souboru XML s pouze veřejné parametry.|  
|Import veřejného klíče|Načte klíče ze souboru XML do kontejneru klíčů.|  
|Testování aplikace|Uvádí postupy pro testování této aplikace.|  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Odkazy <xref:System.IO> a <xref:System.Security.Cryptography> obory názvů.  
  
## <a name="creating-a-windows-forms-application"></a>Vytvoření aplikace Windows Forms  
 Většina příkladů kódu v tomto názorném postupu jsou navržené tak, aby obslužné rutiny událostí pro ovládací prvky tlačítek. Následující tabulka uvádí prvky, které jsou vyžadovány pro ukázkovou aplikaci a požadovaná názvy v příkladech kódu.  
  
|Ovládací prvek|Název|Vlastnost text (podle potřeby)|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|Šifrování souboru|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|Dešifrování souboru|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|Vytvoření klíčů|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|Export veřejného klíče|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|Import veřejného klíče|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|Získání privátní klíč|  
|<xref:System.Windows.Forms.Label>|`label1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 Dvakrát klikněte na tlačítka v návrháři aplikace Visual Studio k vytvoření své obslužné rutiny události.  
  
## <a name="declaring-global-objects"></a>Deklarace globálních objektů  
 Přidejte následující kód do konstruktoru formuláře. Upravte proměnné řetězce pro vaše prostředí a předvolbám.  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a>Vytváření asymetrický klíč  
 Tato úloha vytváří asymetrický klíč, který šifruje a dešifruje <xref:System.Security.Cryptography.RijndaelManaged> klíč. Tento klíč se použil k zašifrování obsahu a zobrazí se název kontejneru klíčů na ovládací prvek popisku.  
  
 Přidejte následující kód, jako `Click` obslužné rutiny události pro `Create Keys` tlačítko (`buttonCreateAsmKeys_Click`).  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a>Šifrování souboru  
 Tato úloha zahrnuje dvě metody: metoda obslužné rutiny události pro `Encrypt File` tlačítko (`buttonEncryptFile_Click`) a `EncryptFile` metoda. První metoda zobrazí dialogové okno pro výběr souboru a předá název souboru druhá metoda, která provádí šifrování.  
  
 Šifrovaný obsah, klíč a vektor IV všechna uložena do jedné <xref:System.IO.FileStream>, což se označuje jako balíčku šifrování.  
  
 `EncryptFile` Metoda provede následující akce:  
  
1.  Vytvoří <xref:System.Security.Cryptography.RijndaelManaged> symetrický algoritmus šifrování obsahu.  
  
2.  Vytvoří <xref:System.Security.Cryptography.RSACryptoServiceProvider> objektu k šifrování <xref:System.Security.Cryptography.RijndaelManaged> klíč.  
  
3.  Používá <xref:System.Security.Cryptography.CryptoStream> objekt ke čtení a šifrování <xref:System.IO.FileStream> zdrojového souboru, v blocích po bajtů do cílového <xref:System.IO.FileStream> objektu pro šifrovaný soubor.  
  
4.  Určuje délky šifrovaný klíč a vektor IV a vytvoří jejich hodnoty pro délku pole bajtů.  
  
5.  Zapíše klíče, IV a jejich hodnoty pro délku zašifrovaný balíček.  
  
 Balíček šifrování používá následující formát:  
  
-   Délka klíče, bajty 0 – 3  
  
-   Vektor IV délka, bajty 4 – 7  
  
-   Šifrovaný klíč  
  
-   VEKTOR IV  
  
-   Šifrovaného textu  
  
 Délek klíč a vektor IV můžete použít k určení počátečních bodů a délek všech částí šifrování balíček, který je pak možné dešifrovat soubor.  
  
 Přidejte následující kód, jako `Click` obslužné rutiny události pro `Encrypt File` tlačítko (`buttonEncryptFile_Click`).  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 Přidejte následující `EncryptFile` metoda do formuláře.  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a>Dešifrování souboru  
 Tato úloha zahrnuje dvě metody, metoda obslužné rutiny události pro `Decrypt File` tlačítko (`buttonDecryptFile_Click`) a `DecryptFile` metoda. První metoda zobrazí dialogové okno pro výběr souboru a jeho název souboru předá druhá metoda, která provede dešifrování.  
  
 `Decrypt` Metoda provede následující akce:  
  
1.  Vytvoří <xref:System.Security.Cryptography.RijndaelManaged> symetrický algoritmus k dešifrování obsahu.  
  
2.  Načte prvních osm bajtů <xref:System.IO.FileStream> šifrované balíčku do pole bajtů k získání délky šifrovaný klíč a vektor IV.  
  
3.  Extrahuje klíč a vektor IV z balíčku šifrování bajtová pole.  
  
4.  Vytvoří <xref:System.Security.Cryptography.RSACryptoServiceProvider> objektu k dešifrování <xref:System.Security.Cryptography.RijndaelManaged> klíč.  
  
5.  Používá <xref:System.Security.Cryptography.CryptoStream> objekt ke čtení a dešifrování části textu šifer <xref:System.IO.FileStream> šifrování balíček, v blocích bajtů do <xref:System.IO.FileStream> objekt dešifrovaný souboru. Po jejím dokončení dešifrování je dokončeno.  
  
 Přidejte následující kód, jako `Click` obslužné rutiny události pro `Decrypt File` tlačítko.  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 Přidejte následující `DecryptFile` metoda do formuláře.  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a>Export veřejného klíče  
 Tato úloha uloží klíč vytvořený `Create Keys` tlačítko do souboru. Exportuje pouze veřejné parametry.  
  
 Tato úloha simuluje scénář Alice poskytuje Bob svůj veřejný klíč tak, aby mohl šifrovat soubory pro ni. On a ostatní, kteří mají tento veřejný klíč nebude možné dešifrovat, protože nemají úplný pár klíče s privátní parametry.  
  
 Přidejte následující kód, jako `Click` obslužné rutiny události pro `Export Public Key` tlačítko (`buttonExportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a>Import veřejného klíče  
 Tato úloha načte klíč s pouze veřejné parametry, jak byly vytvořeny pomocí `Export Public Key` tlačítko a nastaví se jako název kontejneru klíčů.  
  
 Tato úloha simuluje scénář Bob načítání klíče Alice pouze veřejné parametrů tak může šifrovat soubory pro ni.  
  
 Přidejte následující kód, jako `Click` obslužné rutiny události pro `Import Public Key` tlačítko (`buttonImportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a>Získání privátní klíč  
 Tato úloha nastaví název kontejneru klíčů s názvem klíče vytvořeného pomocí `Create Keys` tlačítko. Kontejner klíčů, bude obsahovat úplný pár klíče s privátní parametry.  
  
 Tato úloha simuluje scénář Alici pomocí vlastního soukromého klíče k dešifrování Bob zašifrované soubory.  
  
 Přidejte následující kód, jako `Click` obslužné rutiny události pro `Get Private Key` tlačítko (`buttonGetPrivateKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Po vytvoření aplikace, proveďte následující scénáře testování.  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a>K vytvoření klíčů, šifrování a dešifrování  
  
1.  Klikněte na tlačítko `Create Keys` tlačítko. Popisek zobrazí název klíče a ukazuje, že je úplné klíčový pár.  
  
2.  Klikněte na tlačítko `Export Public Key` tlačítko. Všimněte si, že export veřejného klíče parametry nedojde ke změně aktuálního klíče.  
  
3.  Klikněte na tlačítko `Encrypt File` tlačítko a vyberte soubor.  
  
4.  Klikněte na tlačítko `Decrypt File` tlačítko a vyberte soubor jenom šifrovaná.  
  
5.  Zkontrolujte soubor jenom dešifrovat.  
  
6.  Ukončete aplikaci a restartujte ji otestovat načítání trvalých kontejnerů klíčů obsahuje další scénář.  
  
#### <a name="to-encrypt-using-the-public-key"></a>K šifrování pomocí veřejného klíče  
  
1.  Klikněte na tlačítko `Import Public Key` tlačítko. Popisek zobrazí název klíče a ukazuje, že je veřejný pouze.  
  
2.  Klikněte na tlačítko `Encrypt File` tlačítko a vyberte soubor.  
  
3.  Klikněte na tlačítko `Decrypt File` tlačítko a vyberte soubor jenom šifrovaná. To se nezdaří, protože musí mít privátní klíč pro dešifrování.  
  
 Tento scénář předvádí s pouze veřejný klíč k šifrování souboru pro jinou osobu. Obvykle by tato osoba poskytnout pouze veřejný klíč a odepřít privátní klíč pro dešifrování.  
  
#### <a name="to-decrypt-using-the-private-key"></a>Dešifrování pomocí privátního klíče  
  
1.  Klikněte na tlačítko `Get Private Key` tlačítko. Popisek zobrazí název klíče a ukazuje, zda je úplný pár klíče.  
  
2.  Klikněte na tlačítko `Decrypt File` tlačítko a vyberte soubor jenom šifrovaná. Toto bude úspěšné, protože budete mít úplný pár klíče k dešifrování.  
  
## <a name="see-also"></a>Viz také:

- [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
