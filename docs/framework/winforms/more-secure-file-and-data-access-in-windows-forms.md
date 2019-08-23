---
title: Více zabezpečený přístup k souborům a datům ve Windows Forms
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
ms.openlocfilehash: 94b165757de636b2570798a21fd7c483264e37c5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949954"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Více zabezpečený přístup k souborům a datům ve Windows Forms
.NET Framework používá oprávnění, která vám pomůžou chránit prostředky a data. Kde vaše aplikace může číst nebo zapisovat data, závisí na oprávněních udělených aplikaci. Pokud vaše aplikace běží v prostředí s částečným vztahem důvěryhodnosti, možná nemáte přístup k vašim datům nebo možná budete muset změnit způsob, jakým přistupujete k datům.  
  
 Pokud narazíte na omezení zabezpečení, máte dvě možnosti: vyhodnotit oprávnění (za předpokladu, že byla aplikace udělena), nebo použít verzi funkce zapsanou pro práci v částečném vztahu důvěryhodnosti. Následující části popisují, jak pracovat s přístupem k souborům, databázím a registrům z aplikací, které běží v prostředí s částečným vztahem důvěryhodnosti.  
  
> [!NOTE]
> Ve výchozím nastavení nástroje, které generují nasazení ClickOnce, jsou ve výchozím nastavení tato nasazení, aby požadovaly úplný vztah důvěryhodnosti z počítačů, ve kterých jsou spuštěny. Pokud se rozhodnete, že chcete přidané výhody zabezpečení spouštět v částečném vztahu důvěryhodnosti, je nutné změnit toto výchozí nastavení buď v aplikaci Visual Studio, nebo v některém z Windows SDKch nástrojů (Mage. exe nebo MageUI. exe). Další informace o zabezpečení model Windows Forms a o tom, jak určit odpovídající úroveň důvěryhodnosti pro vaši aplikaci, najdete v tématu [zabezpečení v model Windows Forms přehledu](security-in-windows-forms-overview.md).  
  
## <a name="file-access"></a>Přístup k souborům  
 <xref:System.Security.Permissions.FileIOPermission> Třída řídí přístup k souborům a složkám v .NET Framework. Ve výchozím nastavení systém zabezpečení neuděluje <xref:System.Security.Permissions.FileIOPermission> do prostředí s částečnou důvěryhodností, jako jsou místní intranet a zóny Internet. Aplikace, která vyžaduje přístup k souborům, ale v těchto prostředích můžou pořád fungovat, pokud upravíte návrh aplikace nebo pro přístup k souborům použijete jiné metody. Ve výchozím nastavení má zóna Místní intranet právo mít stejný přístup k webu a stejný přístup k adresáři, aby se mohl připojit zpátky k původnímu serveru a číst z jeho instalačního adresáře. Ve výchozím nastavení je v zóně Internet uděleno právo na zpětné připojení k původnímu serveru.  
  
### <a name="user-specified-files"></a>Soubory zadané uživatelem  
 Jedním ze způsobů, jak se zabývat neoprávněným oprávněním k přístupu k souborům, je vyzvat uživatele k <xref:System.Windows.Forms.OpenFileDialog> zadání <xref:System.Windows.Forms.SaveFileDialog> konkrétních informací o souboru pomocí třídy nebo. Tato interakce uživatele pomáhá zajistit určitou jistotu, že aplikace nemůže škodlivým způsobem načíst soukromé soubory nebo přepsat důležité soubory. Metody <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> a<xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> poskytují přístup pro čtení a zápis souborů otevřením datového proudu souboru pro soubor, který zadal uživatel. Metody také pomůžou chránit soubor uživatele tím, že zakrývá cestu k souboru.  
  
> [!NOTE]
> Tato oprávnění se liší v závislosti na tom, jestli je vaše aplikace v zóně Internet nebo intranetu. Aplikace internetové zóny můžou používat <xref:System.Windows.Forms.OpenFileDialog>jenom, zatímco intranetové aplikace mají oprávnění dialogové okno neomezený soubor.  
  
 <xref:System.Security.Permissions.FileDialogPermission> Třída určuje, jaký typ dialogového okna soubor může vaše aplikace používat. V následující tabulce je uvedena hodnota, kterou je nutné použít pro <xref:System.Windows.Forms.FileDialog> použití jednotlivých tříd.  
  
|Třída|Požadovaná přístupová hodnota|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
> Konkrétní oprávnění není vyžadováno, dokud <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> není metoda skutečně volána.  
  
 Oprávnění k zobrazení dialogového okna soubor neuděluje vaší aplikaci úplný přístup ke všem členům <xref:System.Windows.Forms.FileDialog>tříd, <xref:System.Windows.Forms.OpenFileDialog>a <xref:System.Windows.Forms.SaveFileDialog> . Přesné oprávnění, která jsou vyžadována pro volání jednotlivých metod, naleznete v referenčním tématu pro danou metodu v dokumentaci knihovny tříd .NET Framework.  
  
 Následující příklad kódu používá <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metodu k otevření souboru zadaného uživatelem <xref:System.Windows.Forms.RichTextBox> do ovládacího prvku. Příklad vyžaduje <xref:System.Security.Permissions.FileDialogPermission> a přidruženou <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> hodnotu výčtu. Příklad ukazuje, jak zpracovat, <xref:System.Security.SecurityException> aby bylo možné zjistit, zda by měla být funkce Uložit zakázána. Tento příklad vyžaduje, aby <xref:System.Windows.Forms.Form> <xref:System.Windows.Forms.Button> měl `ButtonOpen` `RtfBoxMain`ovládací prvek s názvem a ovládacíprveksnázvem.<xref:System.Windows.Forms.RichTextBox>  
  
> [!NOTE]
> V tomto příkladu není zobrazená logika programování pro funkci uložit.  
  
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
> V vizuálu C#se ujistěte, že přidáte kód pro povolení obslužné rutiny události. Pomocí kódu z předchozího příkladu následující kód ukazuje, jak povolit obslužnou rutinu události.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Jiné soubory  
 Někdy budete muset číst soubory nebo zapisovat do souborů, které uživatel nezadá, například když musíte zachovat nastavení aplikace. V zóně Místní intranet a Internet nebude vaše aplikace mít oprávnění ukládat data do místního souboru. Vaše aplikace však bude moci ukládat data v izolovaném úložišti. Izolované úložiště je abstraktní datové pole (nejedná se o konkrétní umístění úložiště), které obsahuje jeden nebo víc souborů izolovaného úložiště nazývaných obchody, které obsahují skutečná umístění adresářů, kde jsou data uložená. Nevyžadují <xref:System.Security.Permissions.FileIOPermission> se oprávnění k přístupu k souboru. místo toho <xref:System.Security.Permissions.IsolatedStoragePermission> určuje třída oprávnění pro izolované úložiště. Ve výchozím nastavení můžou aplikace, které běží v místních intranetech a zónách Internetu, ukládat data pomocí izolovaného úložiště; nastavení, jako je disková kvóta, se ale může lišit. Další informace o izolovaném úložišti najdete v tématu [izolované úložiště](../../standard/io/isolated-storage.md).  
  
 Následující příklad používá izolované úložiště k zápisu dat do souboru umístěného v úložišti. Příklad vyžaduje <xref:System.Security.Permissions.IsolatedStorageFilePermission> <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> a hodnotu výčtu. Příklad ukazuje čtení a zápis určitých hodnot <xref:System.Windows.Forms.Button> vlastností ovládacího prvku do souboru v izolovaném úložišti. Funkce by byla volána po spuštění aplikace `Write` a funkce by byla volána před ukončením aplikace. `Read` `Read` Příklad vyžaduje, aby funkce a `Write` existovaly jako členové typu <xref:System.Windows.Forms.Form> , který obsahuje <xref:System.Windows.Forms.Button> ovládací prvek s `MainButton`názvem.  
  
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
 Oprávnění požadovaná pro přístup k databázi se liší v závislosti na poskytovateli databáze. přístup k databázi prostřednictvím datového připojení však mají pouze aplikace, které jsou spuštěny s příslušnými oprávněními. Další informace o oprávněních, která jsou nutná pro přístup k databázi, najdete v tématu [zabezpečení přístupu kódu a ADO.NET](../data/adonet/code-access-security.md).  
  
 Pokud nemůžete získat přímý přístup k databázi, protože chcete, aby se vaše aplikace spouštěla v částečném vztahu důvěryhodnosti, můžete pro přístup k datům použít webovou službu jako alternativní způsob. Webová služba je softwarový software, ke kterému se dá programově přistupovat přes síť. U webových služeb můžou aplikace sdílet data mezi zónami skupin kódu. Ve výchozím nastavení jsou aplikacím v místních intranetech a zónách Internetu udělen právo na přístup k jejich webům původu, což jim umožňuje volat webovou službu hostovanou na stejném serveru. Další informace najdete v tématu [webové služby v ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) nebo [Windows Communication Foundation](../wcf/index.md).  
  
## <a name="registry-access"></a>Přístup k registru  
 <xref:System.Security.Permissions.RegistryPermission> Třída řídí přístup k registru operačního systému. Ve výchozím nastavení mají přístup k registru jenom aplikace, které jsou spuštěné místně.  <xref:System.Security.Permissions.RegistryPermission>udělí aplikaci oprávnění pouze k pokusu o přístup k registru. Nezaručujeme přístup úspěšně, protože operační systém stále vynutil zabezpečení registru.  
  
 Vzhledem k tomu, že nemůžete získat přístup k registru s částečnou důvěryhodností, možná budete muset najít další metody ukládání dat. Při ukládání nastavení aplikace použijte místo registru izolované úložiště. Izolované úložiště lze také použít k ukládání jiných souborů specifických pro aplikaci. Můžete také uložit globální informace o aplikaci o serveru nebo webu původu, protože ve výchozím nastavení je aplikaci uděleno právo na přístup k webu svého původu.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečenější tisk ve Windows Forms](more-secure-printing-in-windows-forms.md)
- [Dodatečné informace o zabezpečení ve Windows Forms](additional-security-considerations-in-windows-forms.md)
- [Přehled zabezpečení ve Windows Forms](security-in-windows-forms-overview.md)
- [Windows Forms – zabezpečení](windows-forms-security.md)
- [Mage.exe (Manifest Generation and Editing Tool)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
