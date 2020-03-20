---
title: Bezpečnější přístup k souborům a datům
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [Windows Forms], file access
- registry [Windows Forms]
- data access [Windows Forms]
- database access (Windows Forms security)
- data [Windows Forms], secure access
- file access [Windows Forms]
- security [Windows Forms], data access
ms.assetid: 3cd3e55b-2f5e-40dd-835d-f50f7ce08967
ms.openlocfilehash: a29c2f7137440e64fbf8095f77d5d10d0505bc2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185902"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Více zabezpečený přístup k souborům a datům ve Windows Forms
Rozhraní .NET Framework používá oprávnění k ochraně prostředků a dat. Kde vaše aplikace může číst nebo zapisovat data závisí na oprávnění udělených aplikaci. Při spuštění aplikace v prostředí částečné důvěryhodnosti, pravděpodobně nemáte přístup k datům nebo budete muset změnit způsob přístupu k datům.  
  
 Pokud narazíte na omezení zabezpečení, máte dvě možnosti: uplatnit oprávnění (za předpokladu, že byla udělena vaší aplikaci) nebo použít verzi funkce napsané pro práci v částečném vztahu důvěryhodnosti. Následující části popisují, jak pracovat s přístupem k souborům, databázím a registru z aplikací spuštěných v prostředí s částečnou důvěryhodností.  
  
> [!NOTE]
> Ve výchozím nastavení nástroje, které generují nasazení ClickOnce, ve výchozím nastavení tato nasazení požadují úplné důvěryhodnosti z počítačů, ve kterých jsou spuštěny. Pokud se rozhodnete, že chcete přidat výhody zabezpečení spuštění v částečném vztahu důvěryhodnosti, musíte změnit toto výchozí nastavení v sadě Visual Studio nebo v jednom z nástrojů sady Windows SDK (Mage.exe nebo MageUI.exe). Další informace o zabezpečení formulářů Windows Forms a o určení odpovídající úrovně důvěryhodnosti aplikace naleznete [v tématu Zabezpečení v Přehledu formulářů systému Windows](security-in-windows-forms-overview.md).  
  
## <a name="file-access"></a>Přístup k souborům  
 Třída <xref:System.Security.Permissions.FileIOPermission> řídí přístup k souborům a složkám v rozhraní .NET Framework. Ve výchozím nastavení systém zabezpečení <xref:System.Security.Permissions.FileIOPermission> neuděluje prostředí částečné důvěryhodnosti, jako je například místní intranet a internetové zóny. Aplikace, která vyžaduje přístup k souborům, však může v těchto prostředích stále fungovat, pokud změníte návrh aplikace nebo pro přístup k souborům použijete různé metody. Ve výchozím nastavení je místní intranetové zóně uděleno právo mít stejný přístup k webu a stejný přístup k adresáři, připojit se zpět k webu svého původu a číst z instalačního adresáře. Ve výchozím nastavení je internetové zóně uděleno pouze právo připojit se zpět k místu, kde je původ.  
  
### <a name="user-specified-files"></a>Soubory zadané uživatelem  
 Jedním ze způsobů, jak se vypořádat s tím, že nemáte <xref:System.Windows.Forms.OpenFileDialog> oprávnění <xref:System.Windows.Forms.SaveFileDialog> k přístupu k souborům, je vyzvat uživatele k zadání konkrétních informací o souboru pomocí třídy nebo. Tato interakce s uživatelem pomáhá poskytnout určitou jistotu, že aplikace nemůže zlomyslně načíst soukromé soubory nebo přepsat důležité soubory. Metody <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> a poskytují přístup k souborům pro čtení a zápis otevřením datového proudu souboru pro soubor, který uživatel zadal. Metody také pomáhají chránit soubor uživatele tím, že zakrývají cestu k souboru.  
  
> [!NOTE]
> Tato oprávnění se liší v závislosti na tom, zda je aplikace v zóně Internet nebo Intranet. Aplikace zóny Internetu mohou <xref:System.Windows.Forms.OpenFileDialog>používat pouze aplikace , zatímco aplikace intranetu mají oprávnění k dialogovému oknu bez omezení.  
  
 Třída <xref:System.Security.Permissions.FileDialogPermission> určuje, jaký typ dialogového okna souboru může aplikace použít. V následující tabulce je uvedena hodnota, <xref:System.Windows.Forms.FileDialog> kterou musíte použít pro každou třídu.  
  
|Třída|Požadovaná hodnota přístupu|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
> Konkrétní oprávnění není požadováno, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> dokud je metoda skutečně volána.  
  
 Oprávnění k zobrazení dialogového okna souboru neuděluje aplikaci <xref:System.Windows.Forms.FileDialog> <xref:System.Windows.Forms.OpenFileDialog>úplný <xref:System.Windows.Forms.SaveFileDialog> přístup všem členům tříd , a tříd. Přesná oprávnění, která jsou vyžadována pro volání jednotlivých metod, naleznete v referenčním tématu pro tuto metodu v dokumentaci ke knihovně tříd rozhraní .NET Framework.  
  
 Následující příklad kódu <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> používá metodu k otevření souboru zadaného uživatelem do ovládacího <xref:System.Windows.Forms.RichTextBox> prvku. Příklad vyžaduje <xref:System.Security.Permissions.FileDialogPermission> a <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> související výčtu hodnotu. Příklad ukazuje, jak zpracovat <xref:System.Security.SecurityException> určit, zda má být zakázána funkce ukládání. Tento příklad vyžaduje, <xref:System.Windows.Forms.Button> aby `ButtonOpen`váš <xref:System.Windows.Forms.Form> má <xref:System.Windows.Forms.RichTextBox> ovládací `RtfBoxMain`prvek s názvem a ovládací prvek s názvem .  
  
> [!NOTE]
> Programovací logika pro funkci uložení není uvedena v příkladu.  
  
```vb  
Private Sub ButtonOpen_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles ButtonOpen.Click
  
    Dim editingFileName as String = ""  
    Dim saveAllowed As Boolean = True  
  
    ' Displays the OpenFileDialog.  
    If (OpenFileDialog1.ShowDialog() = DialogResult.OK) Then  
        Dim userStream as System.IO.Stream  
        Try
            ' Opens the file stream for the file selected by the user.  
            userStream =OpenFileDialog1.OpenFile()
            Me.RtfBoxMain.LoadFile(userStream, _  
                RichTextBoxStreamType.PlainText)  
        Finally  
            userStream.Close()  
        End Try  
  
        ' Tries to get the file name selected by the user.  
        ' Failure means that the application does not have  
        ' unrestricted permission to the file.  
        Try
            editingFileName = OpenFileDialog1.FileName  
        Catch ex As Exception  
            If TypeOf ex Is System.Security.SecurityException Then
                ' The application does not have unrestricted permission
                ' to the file so the save feature will be disabled.  
                saveAllowed = False
            Else
                Throw ex  
            End If  
        End Try  
    End If  
End Sub  
```  
  
```csharp  
private void ButtonOpen_Click(object sender, System.EventArgs e)
{  
    String editingFileName = "";  
    Boolean saveAllowed = true;  
  
    // Displays the OpenFileDialog.  
    if (openFileDialog1.ShowDialog() == DialogResult.OK)
    {  
        // Opens the file stream for the file selected by the user.  
        using (System.IO.Stream userStream = openFileDialog1.OpenFile())
        {  
            this.RtfBoxMain.LoadFile(userStream,  
                RichTextBoxStreamType.PlainText);  
            userStream.Close();  
        }  
  
        // Tries to get the file name selected by the user.  
        // Failure means that the application does not have  
        // unrestricted permission to the file.  
        try
        {  
            editingFileName = openFileDialog1.FileName;  
        }
        catch (Exception ex)
        {  
            if (ex is System.Security.SecurityException)
            {  
                // The application does not have unrestricted permission
                // to the file so the save feature will be disabled.  
                saveAllowed = false;
            }
            else
            {  
                throw ex;  
            }  
        }  
    }  
}  
```  
  
> [!NOTE]
> V jazyce Visual C# se ujistěte, že přidáte kód pro povolení obslužné rutiny události. Pomocí kódu z předchozího příkladu následující kód ukazuje, jak povolit obslužnou rutinu události.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Další soubory  
 Někdy budete muset číst nebo zapisovat do souborů, které uživatel nezadá, například když je nutné zachovat nastavení aplikace. V místních intranetových a internetových zónách nebude mít aplikace oprávnění k ukládání dat do místního souboru. Vaše aplikace však bude moci ukládat data v izolovaném úložišti. Izolované úložiště je abstraktní datový oddíl (nikoli konkrétní umístění úložiště), který obsahuje jeden nebo více izolovaných souborů úložiště, nazývaných úložiště, které obsahují skutečná umístění adresářů, kde jsou uložena data. Oprávnění pro <xref:System.Security.Permissions.FileIOPermission> přístup k souborům nejsou vyžadována. místo toho <xref:System.Security.Permissions.IsolatedStoragePermission> třída řídí oprávnění pro izolované úložiště. Ve výchozím nastavení mohou aplikace spuštěné v místních intranetových a internetových zónách ukládat data pomocí izolovaného úložiště. Nastavení, jako je disková kvóta, se však mohou lišit. Další informace o izolovaném úložišti naleznete v [tématu Izolované úložiště](../../standard/io/isolated-storage.md).  
  
 Následující příklad používá izolované úložiště k zápisu dat do souboru umístěného v úložišti. Příklad vyžaduje <xref:System.Security.Permissions.IsolatedStorageFilePermission> a <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> hodnotu výčtu. Příklad ukazuje čtení a zápis určitých <xref:System.Windows.Forms.Button> hodnot vlastností ovládacího prvku do souboru v izolovaném úložišti. Funkce `Read` bude volána po spuštění `Write` aplikace a funkce bude volána před ukončením aplikace. Příklad vyžaduje, `Read` aby `Write` funkce a existovaly jako <xref:System.Windows.Forms.Button> členové `MainButton`ovládacího <xref:System.Windows.Forms.Form> prvku, který obsahuje ovládací prvek s názvem .  
  
```vb  
' Reads the button options from the isolated storage. Uses Default values
' for the button if the options file does not exist.  
Public Sub Read()
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try  
        ' Checks to see if the options.txt file exists.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
  
            ' Opens the file because it exists.  
            Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _
                 (filename, IO.FileMode.Open,isoStore)  
            Dim reader as System.IO.StreamReader  
            Try
                reader = new System.IO.StreamReader(isos)  
  
                ' Reads the values stored.  
                Dim converter As System.ComponentModel.TypeConverter  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _
                    (GetType(Color))  
  
                Me.MainButton.BackColor = _
                        CType(converter.ConvertFromString _
                         (reader.ReadLine()), Color)  
                me.MainButton.ForeColor = _  
                        CType(converter.ConvertFromString _
                         (reader.ReadLine()), Color)  
  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _
                    (GetType(Font))  
                me.MainButton.Font = _  
                        CType(converter.ConvertFromString _
                         (reader.ReadLine()), Font)  
  
            Catch ex As Exception  
                Debug.WriteLine("Cannot read options " + _  
                    ex.ToString())  
            Finally  
                reader.Close()  
            End Try  
        End If  
  
    Catch ex As Exception  
        Debug.WriteLine("Cannot read options " + ex.ToString())  
    End Try  
End Sub  
  
' Writes the button options to the isolated storage.  
Public Sub Write()
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try
        ' Checks if the file exists, and if it does, tries to delete it.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
            isoStore.DeleteFile(filename)  
        End If  
    Catch ex As Exception  
        Debug.WriteLine("Cannot delete file " + ex.ToString())  
    End Try  
  
    ' Creates the options.txt file and writes the button options to it.  
    Dim writer as System.IO.StreamWriter  
    Try
        Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _
             (filename, IO.FileMode.CreateNew, isoStore)  
  
        writer = New System.IO.StreamWriter(isos)  
        Dim converter As System.ComponentModel.TypeConverter  
  
        converter = System.ComponentModel.TypeDescriptor.GetConverter _
           (GetType(Color))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.BackColor))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.ForeColor))  
  
        converter = System.ComponentModel TypeDescriptor.GetConverter _
           (GetType(Font))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.Font))  
  
    Catch ex as Exception  
        Debug.WriteLine("Cannot write options " + ex.ToString())  
  
    Finally  
        writer.Close()  
    End Try  
End Sub  
```  
  
```csharp  
// Reads the button options from the isolated storage. Uses default values
// for the button if the options file does not exist.  
public void Read()
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try  
    {  
        // Checks to see if the options.txt file exists.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)
        {  
            // Opens the file because it exists.  
            System.IO.IsolatedStorage.IsolatedStorageFileStream isos =
                new System.IO.IsolatedStorage.IsolatedStorageFileStream  
                    (filename, System.IO.FileMode.Open,isoStore);  
            System.IO.StreamReader reader = null;  
            try
            {  
                reader = new System.IO.StreamReader(isos);  
  
                // Reads the values stored.  
                TypeConverter converter ;  
                converter = TypeDescriptor.GetConverter(typeof(Color));  
  
                this.MainButton.BackColor =
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
                this.MainButton.ForeColor =
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
  
                converter = TypeDescriptor.GetConverter(typeof(Font));  
                this.MainButton.Font =
                  (Font)(converter.ConvertFromString(reader.ReadLine()));  
            }  
            catch (Exception ex)  
            {
                System.Diagnostics.Debug.WriteLine  
                     ("Cannot read options " + ex.ToString());  
            }  
            finally  
            {  
                reader.Close();  
            }  
        }  
    }
    catch (Exception ex)
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot read options " + ex.ToString());  
    }  
}  
  
// Writes the button options to the isolated storage.  
public void Write()
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try
    {  
        // Checks if the file exists and, if it does, tries to delete it.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)
        {  
            isoStore.DeleteFile(filename);  
        }  
    }  
    catch (Exception ex)
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot delete file " + ex.ToString());  
    }  
  
    // Creates the options file and writes the button options to it.  
    System.IO.StreamWriter writer = null;  
    try
    {  
        System.IO.IsolatedStorage.IsolatedStorageFileStream isos = new
            System.IO.IsolatedStorage.IsolatedStorageFileStream(filename,
            System.IO.FileMode.CreateNew,isoStore);  
  
        writer = new System.IO.StreamWriter(isos);  
        TypeConverter converter ;  
  
        converter = TypeDescriptor.GetConverter(typeof(Color));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.BackColor));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.ForeColor));  
  
        converter = TypeDescriptor.GetConverter(typeof(Font));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.Font));  
  
    }  
    catch (Exception ex)  
    {
        System.Diagnostics.Debug.WriteLine  
           ("Cannot write options " + ex.ToString());  
    }  
    finally  
    {  
        writer.Close();  
    }  
}  
```  
  
## <a name="database-access"></a>Přístup k databázi  
 Oprávnění požadovaná pro přístup k databázi se liší v závislosti na poskytovateli databáze. pouze aplikace, které jsou spuštěny s příslušnými oprávněními, však mohou přistupovat k databázi prostřednictvím datového připojení. Další informace o oprávněních, která jsou vyžadována pro přístup k databázi, naleznete v [tématu Zabezpečení přístupu kódu a ADO.NET](../data/adonet/code-access-security.md).  
  
 Pokud nelze přímo přistupovat k databázi, protože chcete, aby aplikace spustit v částečném vztahu důvěryhodnosti, můžete použít webovou službu jako alternativní prostředek pro přístup k datům. Webová služba je software, ke kterému lze programově přistupovat prostředně prostředně. Pomocí webových služeb mohou aplikace sdílet data mezi zónami kódových skupin. Ve výchozím nastavení je aplikacím v místní chu-intranetu a internetových zónách uděleno právo na přístup k jejich webům původu, což jim umožňuje volat webovou službu hostovanou na stejném serveru. Další informace naleznete [v tématu Webové služby v ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) nebo Windows Communication [Foundation](../wcf/index.md).  
  
## <a name="registry-access"></a>Přístup k registru  
 Třída <xref:System.Security.Permissions.RegistryPermission> řídí přístup k registru operačního systému. Ve výchozím nastavení mohou k registru přistupovat pouze aplikace, které jsou spuštěny místně.  <xref:System.Security.Permissions.RegistryPermission>pouze uděluje aplikaci právo vyzkoušet přístup k registru; nezaručuje, že přístup bude úspěšný, protože operační systém stále vynucuje zabezpečení v registru.  
  
 Vzhledem k tomu, že nelze získat přístup k registru pod částečným vztahem důvěryhodnosti, bude pravděpodobně nutné najít jiné metody ukládání dat. Při ukládání nastavení aplikace použijte místo registru izolované úložiště. Izolované úložiště lze také použít k ukládání jiných souborů specifických pro aplikaci. Můžete také ukládat informace o globální aplikaci o serveru nebo webu původu, protože ve výchozím nastavení je aplikaci uděleno právo na přístup k webu svého původu.  
  
## <a name="see-also"></a>Viz také

- [Bezpečnější tisk ve Windows Forms](more-secure-printing-in-windows-forms.md)
- [Dodatečné informace o zabezpečení ve Windows Forms](additional-security-considerations-in-windows-forms.md)
- [Přehled zabezpečení ve Windows Forms](security-in-windows-forms-overview.md)
- [Windows Forms – zabezpečení](windows-forms-security.md)
- [Mage.exe (Manifest Generation and Editing Tool)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
