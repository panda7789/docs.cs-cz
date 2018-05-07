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
ms.openlocfilehash: 5db6fc886fe53fb60d38471bd463868ce2f37fc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Více zabezpečený přístup k souborům a datům ve Windows Forms
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Využívá oprávnění k ochraně prostředkům a datům. Kde vaše aplikace můžou číst nebo zapisovat data závisí na oprávněních udělených aplikaci. Když aplikace běží v prostředí s částečnou důvěryhodností, pravděpodobně nebudete mít přístup k datům nebo možná budete muset změnit způsob přístupu k datům.  
  
 Když dojde k omezení zabezpečení, máte dvě možnosti: uplatnit oprávnění (za předpokladu, že byla udělena do aplikace), nebo použijte verzi funkci určený pro práci v částečné důvěryhodnosti. Následující části popisují, jak pracovat s soubor, databáze a přístup k registru z aplikací, které běží v prostředí s částečnou důvěryhodností.  
  
> [!NOTE]
>  Ve výchozím nastavení nástroje, které generují [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] nasazení výchozí tato nasazení na vyžádání úplný vztah důvěryhodnosti z počítačů, na kterých poběží. Pokud se rozhodnete chcete využít výhod zvýšení zabezpečení spuštěných v částečné důvěryhodnosti, musíte změnit toto výchozí nastavení v sadě Visual Studio nebo jeden z [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] nástroje (Mage.exe nebo MageUI.exe). Další informace o zabezpečení Windows Forms a o způsobu určení úrovně důvěryhodnosti vhodné pro vaše aplikace najdete v tématu [zabezpečení ve Windows Forms přehled](../../../docs/framework/winforms/security-in-windows-forms-overview.md).  
  
## <a name="file-access"></a>Přístup k souborům  
 <xref:System.Security.Permissions.FileIOPermission> Třídy ovládacích prvků přístupu souborů a složek v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Ve výchozím nastavení, systém zabezpečení nejsou udělena <xref:System.Security.Permissions.FileIOPermission> do prostředí částečné důvěryhodnosti například místního intranetu a Internetu zóny. Aplikaci, která vyžaduje přístup k souborům mohou však i nadále fungovat v těchto prostředích Pokud změníte návrh aplikace nebo použít různé metody pro přístup k souborům. Ve výchozím nastavení je zóny místního intranetu uděleno právo mají stejný přístup k serveru a stejný přístup directory zpětné připojení k původnímu serveru a čtení z jeho instalační adresář. Ve výchozím nastavení je zóně Internet, pouze uděleno právo připojit zpět k původnímu serveru.  
  
### <a name="user-specified-files"></a>Soubory definované uživatelem  
 Jedním ze způsobů, jak nakládat s nemá přístup k souborům oprávnění je vyzvat uživatele k zadání informací o konkrétní souboru pomocí <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog> třídy. Tato interakce uživatele pomáhá poskytovat některé záruku, že aplikace nemůže neoprávněnému načíst soubory soukromých nebo přepsat důležitých souborů. <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> a <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> poskytují metody pro čtení a zápis přístup k souborům otevřením datový proud souboru pro soubor, který uživatel zadal. Metody také chránit soubor uživatele zakódováním cestu souboru.  
  
> [!NOTE]
>  Tato oprávnění se liší v závislosti na tom, jestli vaše aplikace je v zóně Internet nebo zóny intranetu. Internetové zóny aplikace lze použít pouze <xref:System.Windows.Forms.OpenFileDialog>, zatímco aplikace v síti Intranet mají neomezený souboru dialogové okno oprávnění.  
  
 <xref:System.Security.Permissions.FileDialogPermission> Třída určuje, jaký typ dialogového okna souboru aplikace můžete používat. Následující tabulka uvádí hodnotu, musí mít použití každé <xref:System.Windows.Forms.FileDialog> třídy.  
  
|Třída|Hodnota požadovaný přístup|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
>  Dokud není požadována konkrétní oprávnění <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> ve skutečnosti volání metody.  
  
 Oprávnění k zobrazit dialogové okno souboru neuděluje úplný přístup k vaší aplikaci do všech členů <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, a <xref:System.Windows.Forms.SaveFileDialog> třídy. Přesný oprávnění, která jsou nutná k volání každou metodu, najdete v tématu referenční téma pro tuto metodu v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] třídy dokumentaci ke knihovně.  
  
 Následující příklad kódu používá <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda pro otevření souboru do zadaného uživatelem <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Příklad vyžaduje <xref:System.Security.Permissions.FileDialogPermission> a přidružené <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> hodnota výčtu. Příklad ukazuje, jak bude zpracováván <xref:System.Security.SecurityException> k určení zda uložení funkce by mělo být zakázáno. Tento příklad vyžaduje, aby vaše <xref:System.Windows.Forms.Form> má <xref:System.Windows.Forms.Button> ovládací prvek s názvem `ButtonOpen`a <xref:System.Windows.Forms.RichTextBox> ovládací prvek s názvem `RtfBoxMain`.  
  
> [!NOTE]
>  Programovací logiku pro uložení funkce není uvedeno v příkladu.  
  
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
>  V jazyce Visual C#, ujistěte se, že přidáte kód, aby obslužná rutina události. Pomocí kódu z předchozího příkladu následující kód ukazuje, jak povolit obslužné rutiny události.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Ostatní soubory  
 Někdy můžete potřebovat pro čtení nebo zápis do souborů, že uživatel není uveden, například když musí zachovat nastavení aplikace. V místní intranet a Internet zóny vaše aplikace nebude mít oprávnění k uložení dat v případě místního souboru. Aplikace však bude možné k ukládání dat v izolovaném úložišti. Izolované úložiště je abstraktní datového oddílu (ne umístění konkrétní úložiště), který obsahuje jeden nebo více souborů izolovaného úložiště volaných úložišť, které obsahují skutečné directory umístění, kde jsou data uložena. Soubor oprávnění k přístupu, jako je <xref:System.Security.Permissions.FileIOPermission> nejsou vyžadovány; místo toho <xref:System.Security.Permissions.IsolatedStoragePermission> třída řídí oprávnění pro izolované úložiště. Ve výchozím nastavení může aplikace, které jsou spuštěné v místním intranetu a Internetu zón ukládat data pomocí izolované úložiště. nastavení, jako je disková kvóta se však může lišit. Další informace o izolovaného úložiště najdete v tématu [izolované úložiště](../../../docs/standard/io/isolated-storage.md).  
  
 Následující příklad používá izolované úložiště k zápisu dat do souboru umístěný v úložišti. Příklad vyžaduje <xref:System.Security.Permissions.IsolatedStorageFilePermission> a <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> hodnota výčtu. Příklad ukazuje, čtení a zápisu určitých hodnot vlastností <xref:System.Windows.Forms.Button> ovládacího prvku do souboru v izolovaném úložišti. `Read` Funkce by být volána po spuštění aplikace a `Write` funkce by být volána před ukončením aplikace. Tento příklad vyžaduje, aby `Read` a `Write` funkce existovat jako členy <xref:System.Windows.Forms.Form> obsahující <xref:System.Windows.Forms.Button> ovládací prvek s názvem `MainButton`.  
  
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
 Oprávnění požadovaná pro přístup k databázi lišit v závislosti na poskytovateli databáze; pouze aplikace, které běží s příslušnými oprávněními ale může přístup k databázi prostřednictvím datového připojení. Další informace o oprávněních, která jsou nutné pro přístup k databázi najdete v tématu [zabezpečení přístupu kódu a ADO.NET](../../../docs/framework/data/adonet/code-access-security.md).  
  
 Pokud databázi nelze přistupovat přímo, protože chcete, aby aplikace na spouštění v částečné důvěryhodnosti, můžete jako alternativní prostředek pro přístup k datům webové služby. Webová služba je softwarového produktu, který lze programově přistupovat přes síť. S webovými službami můžou aplikace sdílet data mezi zón skupiny kódu. Ve výchozím nastavení je aplikace v místním intranetu a Internetu zón uděleno oprávnění k přístupu k jejich lokality původu, která umožňuje, aby volání webové služby hostované na stejném serveru. Další informace najdete v části [webových služeb v rozhraní ASP.NET AJAX](http://msdn.microsoft.com/library/8290e543-7eff-47a4-aace-681f3c07229b) nebo [Windows Communication Foundation](http://msdn.microsoft.com/library/ms735119.aspx).  
  
## <a name="registry-access"></a>Přístup k registru  
 <xref:System.Security.Permissions.RegistryPermission> Třída řídí přístup k registru operačního systému. Ve výchozím nastavení můžete jenom aplikace, které běží místně přistupovat k registru.  <xref:System.Security.Permissions.RegistryPermission> aplikaci jenom uděluje práva k zkuste přístup k registru; se nezaručuje, že přístup bude úspěšné, protože operační systém stále vynucuje zabezpečení v registru.  
  
 Protože nelze získat přístup k registru v částečné důvěryhodnosti, musíte k nalezení dalších metod ukládání dat. Při ukládání nastavení aplikace pomocí izolovaného úložiště místo registru. Izolovaná úložiště lze také ukládat další soubory specifické pro aplikaci. Globální aplikace informace o serveru nebo webu původu, také můžete uložit, protože ve výchozím nastavení aplikace jsou udělena oprávnění k přístupu k původnímu serveru.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečenější tisk ve Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 [Dodatečné informace o zabezpečení ve Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [Přehled zabezpečení ve Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Windows Forms – zabezpečení](../../../docs/framework/winforms/windows-forms-security.md)  
 [Mage.exe (Manifest Generation and Editing Tool)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
