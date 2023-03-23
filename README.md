# verifyTitle-Selenium
selenium framework
package ui;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.testng.Assert;
import org.testng.annotations.Test;
import org.testng.asserts.SoftAssert;

import io.github.bonigarcia.wdm.WebDriverManager;
//SOFT Asseration HARD Asseration
public class VerifyTitleTest {
	@Test
	public void titletest() {
		//SoftAssert softassert =new SoftAssert();
		String expectedtitle = "Electronics, Cars, Fashion, Collectibles & More | eBay";
		String expectedText ="Search";
		ChromeOptions co = new ChromeOptions();
		co.addArguments("--remote-allow-origins=*");
		WebDriverManager.chromedriver().setup();
		WebDriver driver = new ChromeDriver(co);
		driver.get("https://www.ebay.com/");
		driver.get("https://www.amazon.com/");
		driver.get("https://www.yahoo.com/?guccounter=1");
		driver.get("https://www.lendingtree.com/");
		driver.get("https://www.apple.com/");
		driver.get("https://www.business.com/");
		driver.get("https://www.zoho.com/");
		driver.get("https://www.food.com/");
		//driver.get("https://www.maldives.com/");
		driver.get("https://travel.com/");
		driver.get("https://chat.openai.com/chat");
		driver.get("https://openai.com/blog/chatgpt");
		
		String actualtitle = driver.getTitle();
		System.out.println("Verifying Title");
		//softassert.assertEquals(actualtitle, expectedText, "Title verification pass");
		Assert.assertEquals(actualtitle, expectedtitle,"Title verification pass");
		String actualText = driver.findElement(By.xpath("//*[@id=\"gh-btn\"]")).getAttribute("value");
		//softassert.assertEquals(actualText, expectedText,"Text verification pass");
		Assert.assertEquals(actualText, expectedText, "Test verification pass");
		//System.out.println("Closing browser");
		//driver.close();
		//softassert.assertAll();
		
	}

}

