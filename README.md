# Live Project Code Summary

Introduction

At the end of The Tech Academy's bootcamp I did a two week Live Project with fellow Tech Academy Students. We worked on an ASP.NET MVC Webapp using a code first database model with Entity Framework. 

**Front End**

I worked on styling a create form using HTML and CSS for the site we were working on. The HTML was mostly in place by the time I started working on it but it was using a lot of bootstrap classes. I removed some bootstrap classes and added my own classes to them. 

Here is the CSS I created for the page:
    
   ```
    .formContainer {
    display: block;
    margin-left: auto;
    margin-right: auto;
    text-align: center;
    max-width: 30%;
    background-color: var(--main-secondary-color);
    background-image: linear-gradient(var(--light-color), var(--main-secondary-color));
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    border-radius: 2px;
    font-family: 'Lato Hairline';
    animation-duration: 5s;
    -webkit-animation-duration: 5s;
    animation-name: fadeIn;
    -webkit-animation-name: fadeIn;
    }
    
@-webkit-keyframes fadeIn {
    0% { opacity: 0; }

    100% { opacity: .1; }
}

@keyframes fadeIn {
    0% { opacity: 0; }

    100% { opacity: 1; }
}

.formHeader {
    color: var(--dark-color);
    font-family: Lato;
    letter-spacing: 3px;
    font-size: 40px;
    font-weight: 400;
    padding-top: 20px;
    padding-bottom: 20px;
}

.inputBox {
    color: var(--dark-color);
    margin-left: auto;
    margin-right: auto;
    padding-bottom: 15px;
    max-width: 50%;
    letter-spacing: 1px;
    font-size: 15px;
    font-weight: bolder;
    animation-duration: 10s;
    -webkit-animation-duration: 10s;
    animation-name: fadeIn2;
    -webkit-animation-name: fadeIn2;
}

@-webkit-keyframes fadeIn2 {
    0% { opacity: 0; }

    100% { opacity: 1; }
}

@keyframes fadeIn2 {
    0% { opacity: 0; }

    100% { opacity: 1; }
}

.inputText {
    color: var(--dark-color);
    font-family: Lato;
    border: none;
    border-radius: 4px 4px 0px 0px;
    border-bottom: 2px solid var(--dark-color);
}

.submitButton {
    display: inline-block;
    width: 75%;
    letter-spacing: 1px;
    font-family: Lato;
    font-weight: 500;
    padding: 10px 0px;
    margin: 10px auto 10px auto;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    border: 0px solid;
    border-color: var(--dark-color);
    color: var(--light-color);
    background-color: var(--secondary-color);
    text-align: center;
    vertical-align: middle;
    font-size: 1rem;
    line-height: 1.5;
    border-radius: 15px;
    user-select: none;
    transition: all .5s;
    box-shadow: 0px 4px #999;
    animation-duration: 10s;
    -webkit-animation-duration: 10s;
    animation-name: fadeIn3;
    -webkit-animation-name: fadeIn3;
}

@-webkit-keyframes fadeIn3 {
    0% { opacity: 0; }

    100% { opacity: 1; }
}

@keyframes fadeIn3 {
    0% { opacity: 0; }

    100% { opacity: 1; }
}

.submitButton:hover {
    color: var(--dark-color);
    background-color: var(--main-bg-color);
}

.submitButton:active {
    background-color: var(--main-bg-color);
    box-shadow: 0px 0px #666;
    transform: translateY(2px)
}
```

**Back End**

There was a create form in the site that had a checkbox that users can click. I changed that so depending on the answers they entered on other form inputs that check box would automatically check itself or stay blank. I then removed the check box from the view so a user couldn't click it. 

This is the logic I created to allow that to happen:

```
 if (ModelState.IsValid)
            {
                ViewData["dbUsers"] = new SelectList(db.Users.ToList(), "Id", "UserName");
                seasonManager.SeasonManagerPerson = db.Users.Find(userId);
                db.SeasonManagers.Add(seasonManager);               
                if (seasonManager.FallTime != null)
                {
                    seasonManager.BookedFall = true;
                }
                if (seasonManager.WinterTime != null)
                {
                    seasonManager.BookedWinter = true;
                }
                if (seasonManager.SpringTime != null)
                {
                    seasonManager.BookedSpring = true;
                }
                db.SaveChanges();
                return RedirectToAction("Index");
            }
            return View(seasonManager);
        }       
```
